# deconz

![Version: 6.5.2](https://img.shields.io/badge/Version-6.5.2-informational?style=flat-square) ![AppVersion: 2.12.06](https://img.shields.io/badge/AppVersion-2.12.06-informational?style=flat-square)

deCONZ is an easy to use control software, with which you can set up and control Zigbee networks of any size without further programming effort.

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/dresden-elektronik/deconz-rest-plugin>
* <https://github.com/deconz-community/deconz-docker>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://library-charts.k8s-at-home.com | common | 4.5.2 |

## TL;DR

```console
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install deconz k8s-at-home/deconz
```

## Installing the Chart

To install the chart with the release name `deconz`

```console
helm install deconz k8s-at-home/deconz
```

## Uninstalling the Chart

To uninstall the `deconz` deployment

```console
helm uninstall deconz
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common/values.yaml) from the [common library](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install deconz \
  --set env.TZ="America/New York" \
    k8s-at-home/deconz
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install deconz k8s-at-home/deconz -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Affinity constraint rules to place the Pod on a specific node. [[ref]](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#affinity-and-anti-affinity) |
| env | object | See below | environment variables. See [image docs](https://github.com/marthoc/docker-deconz/blob/master/README.md) for more details. |
| env.DECONZ_DEVICE | string | `nil` | Override the location where deCONZ looks for the RaspBee/Conbee device. |
| env.DECONZ_VNC_MODE | int | `1` | Enable VNC access to the container to view the deCONZ ZigBee mesh |
| env.DECONZ_VNC_PASSWORD | string | `nil` | If VNC is enabled (DECONZ_VNC_MODE=1) you can change the default password "changeme" using a Secret. |
| env.DECONZ_VNC_PORT | int | `5900` | VNC server listen port |
| env.DECONZ_WEB_PORT | int | `80` | Web UI listen port |
| env.DECONZ_WS_PORT | int | `443` | Websocket listen port |
| env.TZ | string | `"UTC"` | Set the container timezone |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"deconzcommunity/deconz"` | image repository |
| image.tag | string | `"2.12.06"` | image tag |
| ingress.main | object | See values.yaml | Enable and configure ingress settings for the chart under this key. |
| persistence | object | See values.yaml | Configure persistence settings for the chart under this key. |
| persistence.usb | object | See values.yaml | Configure a hostPathMount to mount a USB device in the container. |
| securityContext.privileged | bool | `nil` | Privileged securityContext may be required if USB controller is accessed directly through the host machine |
| service | object | See values.yaml | Configures service settings for the chart. |

## Changelog

### Version 6.5.2

#### Added

N/A

#### Changed

* Upgraded `common` chart dependency to version 4.5.2

#### Fixed

N/A

### Older versions

A historical overview of changes can be found on [ArtifactHUB](https://artifacthub.io/packages/helm/k8s-at-home/deconz?modal=changelog)

## Support

- See the [Docs](https://docs.k8s-at-home.com/our-helm-charts/getting-started/)
- Open an [issue](https://github.com/k8s-at-home/charts/issues/new/choose)
- Ask a [question](https://github.com/k8s-at-home/organization/discussions)
- Join our [Discord](https://discord.gg/sTMX7Vh) community

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v0.1.1](https://github.com/k8s-at-home/helm-docs/releases/v0.1.1)