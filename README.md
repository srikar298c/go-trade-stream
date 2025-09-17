# go-trade-stream-prototype

`go-trade-stream` is a **real-time stock trading and analytics platform prototype** built with **Go**, showcasing how to integrate **RabbitMQ** (for reliable event-driven messaging) and **Kafka** (for high-throughput streaming).

This project is designed for developers who want to understand **event-driven architecture** and **streaming systems** in practice, especially within the context of financial applications.

---

## ✨ Features

* **Order Service (RabbitMQ)** – Handles buy/sell orders and ensures reliable delivery.
* **Market Data Service (Kafka)** – Streams live stock prices into Kafka topics.
* **Portfolio Service (RabbitMQ + Kafka)** – Tracks user portfolios, trade executions, and valuations.
* **Analytics Service (Kafka Streams)** – Processes market data in real-time for insights (e.g., moving averages, top gainers).
* **Observability** – Metrics, logs, and tracing for debugging and monitoring.
* **Resilient Messaging** – Retry policies, dead-letter queues, and fault tolerance.
* **Scalable Architecture** – Built with modular microservices for horizontal scaling.

---

## 🎯 Learning Goals

* Understand **RabbitMQ vs Kafka** use cases.
* Learn **publish/subscribe, fanout, and consumer group** messaging patterns.
* Explore **Go microservices** with event-driven communication.
* Implement **fault tolerance, retries, and dead-letter queues**.
* Gain insights into **production-grade fintech system design**.

---

## 🏗️ Architecture Overview

```plaintext
           +------------------+
           |   Order Service  |
           |  (Go + RabbitMQ) |
           +------------------+
                    |
                    v
            [ RabbitMQ Exchange ]
                    |
                    v
           +------------------+
           | Portfolio Service|
           | (Go Consumer)    |
           +------------------+
                    ^
                    |
   +-----------------------------------+
   |                                   |
   v                                   |
[ Kafka: stock-prices topic ]          |
   |                                   |
   v                                   |
+-------------------+          +------------------+
| Market Data Svc   |          | Analytics Service|
| (Go + Kafka Prod) |          | (Go + Kafka Cons)|
+-------------------+          +------------------+
```

---

## 📂 Project Structure

```
go-trade-stream/
├── order-service/        # Handles orders (RabbitMQ producer)
├── market-data-service/  # Streams stock prices (Kafka producer)
├── portfolio-service/    # Updates portfolios (RabbitMQ + Kafka consumer)
├── analytics-service/    # Real-time analytics (Kafka consumer/streams)
├── pkg/                  # Shared utilities (logging, config, middleware)
├── deployments/          # Docker Compose, infra configs
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

* [Go 1.22+](https://go.dev/)
* [Docker](https://www.docker.com/)
* [RabbitMQ](https://www.rabbitmq.com/)
* [Apache Kafka](https://kafka.apache.org/)

### Setup

```bash
# Clone the repo
git clone https://github.com/your-username/go-trade-stream.git
cd go-trade-stream

# Start infra (RabbitMQ + Kafka)
docker-compose up -d

# Run a service (example: order-service)
cd order-service
go run main.go
```

---

## 🔍 Observability & Monitoring

* **Prometheus metrics** exposed at `/metrics`.
* **Structured logging** with contextual fields for tracing.
* **OpenTelemetry integration** for distributed tracing.
* **Grafana dashboards** to visualize system health.

---

## 📚 Use Cases

* Learn **event-driven microservices** in Go.
* Explore integration of **RabbitMQ and Kafka** in one architecture.
* Prototype **real-time trading & analytics systems**.
* Teach teams about **scalable system design patterns**.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!
Feel free to fork this repo, open issues, and submit PRs.

---

## 🌍 Roadmap

* [ ] Add WebSocket gateway for real-time price updates to clients.
* [ ] Extend analytics with more financial indicators.
* [ ] Add authentication & user management.
* [ ] Kubernetes deployment manifests.

---

## 📜 License

MIT License. Free to use, modify, and share.

---
