---
title: Port Forwarding
---
# Port Forwarding
!!! info "About Tunnel feature (a.k.a Port Forwarding)"
    WebSSH's Tunnel feature will let you to enable [Local Port Forwarding (LPF)](https://en.wikipedia.org/wiki/Port_forwarding#Local_port_forwarding) and [Dynamic Port Forwarding (DPF)](https://en.wikipedia.org/wiki/Port_forwarding#Dynamic_port_forwarding).
    LPF and DPF will let you to connect from your iDevice to another server while data is securely forwarded using SSH protocol in the following way :
    
    * LPF will forward a local port on your iDevice to a remote IP and port through your SSH server
    * DPF will forward all connections *INSIDE* WebSSH (SSH, SFTP) to a dynamic remote IP and port through your SSH server (aka bastion)

## Local Port Forwarding
### How to use it?
1. Add a new tunnel by choossing **Tunnel** tab and by pessing the **+** button
2. Fill all required fields in order to establish the SSH connection
3. Finally choose the remote server port you want to forward locally by using the right syntax
4. Save the tunnel and launch it
5. You are now able to connect to your choosed local port

!!! tip "Port Forwarding Syntax"
    The Port Forwarding Syntax is as simple as : **LOCAL_PORT:REMOTE_SERVER:REMOTE_PORT**

!!! abstract "Port Forwarding Examples"
    * **8080:localhost:80** will forward remote port 80 (on the same server as the SSH one) to local port 8080
    * **3389:localhost:3389** will forward remote port 3389 (on the same server as the SSH one) to local port 3389
    * **2222:172.16.0.18:22** will forward remote port 22 (on the server 172.16.0.18) to local port 2222

## Dynamic Port Forwarding
### How to use it?
1. Add a new tunnel by choossing **Tunnel** tab and by pessing the **+** button
2. Fill all required fields in order to establish the SSH connection
3. Finally put the magical word inside the port fowarding field, a simple wildcard character : *
4. Save the tunnel and launch it
5. You are now able to launch any SSH or SFTP connection inside WebSSH through your bastion

## How Port Forwarding works inside WebSSH?
Behind the scene WebSSH uses [Network Extension](https://developer.apple.com/documentation/networkextension) inside your iDevice in order to setup a [Packet Tunnel Provider](https://developer.apple.com/documentation/networkextension/packet_tunnel_provider).

!!! question "Why WebSSH is requesting to add VPN configuration?"
    When starting a tunnel for the first time you will encounter the following prompt :
    > "WebSSH" Would Like to Add VPN Configurations
    >
    > All network activity on this iDevice may be filtered or monitored when using VPN.

    [Packet Tunnel Provider](https://developer.apple.com/documentation/networkextension/packet_tunnel_provider) - used by WebSSH and provided by Apple - is designed to implement a packet-oriented custom VPN protocol, so it's why this prompt is displayed.
    WebSSH will never forward your data to any external server. Your data will never leave your iDevice except to your own SSH server!

If you need more help about this feature, please open a [how to](https://github.com/isontheline/pro.webssh.net/issues/new?assignees=&labels=&template=how_to.md&title=) issue.