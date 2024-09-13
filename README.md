# RabbitMQ Development Environment

This repo uses a Nix flake to set up a RabbitMQ development environment. It provides an isolated environment with RabbitMQ server and necessary tools.

## Prerequisites

- Nix package manager with flakes enabled [download](https://nixos.org/download.html)

## Setup

1. Clone this repository:
   ```
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Enter the Nix development shell:
   ```
   nix develop
   ```

   This command will download and set up all necessary dependencies, including RabbitMQ server.

3. Once in the Nix shell, you'll see output similar to:
   ```
   RabbitMQ development environment
   Run 'rabbitmq-server' to start RabbitMQ

   RabbitMQ Connection String:
   amqp://guest:guest@localhost:5672

   RabbitMQ data directory: /tmp/rabbitmq-<username>

   Available commands:
     rabbitmq-server    - Start the RabbitMQ server
     rabbitmqctl        - RabbitMQ management tool
     rabbitmq-plugins   - RabbitMQ plugin management tool
   ```

## Starting RabbitMQ

To start the RabbitMQ server, run:

```
rabbitmq-server
```

This will start RabbitMQ in the foreground. To stop it, press Ctrl+C.

## Connecting to RabbitMQ

Use the connection string provided in the shell output to connect to RabbitMQ from your applications. The default connection string is:

```
amqp://guest:guest@localhost:5672
```

- Username: guest
- Password: guest
- Host: localhost
- Port: 5672

## Managing RabbitMQ

- Use `rabbitmqctl` for management tasks (e.g., `rabbitmqctl list_queues`)
- Use `rabbitmq-plugins` to manage plugins (e.g., `rabbitmq-plugins enable rabbitmq_management`)

## Data Persistence

RabbitMQ data is stored in a temporary directory (shown in the shell output). This data will be lost when you reboot your system. For persistent data, modify the `flake.nix` to use a permanent directory.

## Exiting the Environment

To exit the Nix development shell, simply type `exit` or press Ctrl+D.

## Customization

To customize the RabbitMQ configuration or change default settings, modify the `flake.nix` file in this repository.
