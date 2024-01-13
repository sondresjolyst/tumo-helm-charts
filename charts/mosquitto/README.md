# Mosquitto Kubernetes Helm Chart

A Kubernetes Helm Chart for Mosquitto.

## Installation

Install the helm chart repository:

```bash
helm repo add mosquitto https://sondresjolyst.github.io/mosquitto-helm-chart
```

Install the chart:

```bash
helm install mosquitto mosquitto/mosquitto -f your-values.yaml
```

Make release:

```bash
helm package .
helm repo index charts/mosquitto --url https://sondresjolyst.github.io/tumo-helm-charts/charts/mosquitto --merge ../index.yaml
```
## Passwords

Use the software `mosquitto_passwd` to generate the password in the correct format:

```bash
FILE=$(mktemp)
mosquitto_passwd -H sha512-pbkdf2 -c $FILE USERNAME
cut -d ":" -f 2 $FILE
rm $FILE
```