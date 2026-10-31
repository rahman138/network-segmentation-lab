# Segmented Small-Office Network (Cisco Packet Tracer)

A small office network with separate Staff and Guest networks, built and tested in Cisco Packet Tracer. Guests can reach the internet side but are blocked from Staff resources.

## Topology
- 1x Cisco 2911 router (R1)
- 2x Cisco 2960 switches (SW-STAFF, SW-GUEST)
- 4x PCs (2 Staff, 2 Guest)
- 1x DNS server

## Addressing
| Network | VLAN | Subnet | Gateway |
| Staff   | 10   | 192.168.1.0/24 | 192.168.1.1 |
| Guest   | 20   | 192.168.2.0/24 | 192.168.2.1 |
| DNS Server | 10 | 192.168.1.5 | 192.168.1.1 |

## What I configured
- **Routing:** R1 connects both subnets so the networks can communicate
- **VLANs:** VLAN 10 (STAFF) and VLAN 20 (GUEST) on the switches
- **DHCP:** Router hands out addresses, excluding .1 to .10 for infrastructure
- **DNS:** Server at 192.168.1.5 resolves www.mylab.com, handed out via DHCP
- **ACL:** `BLOCK-GUEST` on R1 denies Guest traffic to Staff and permits everything else
- **Port security:** Sticky MAC, max 1 device per port, shutdown on violation (Fa0/1-2)

## Testing results
- PCs received DHCP addresses and gateway automatically
- Staff PCs resolve and reach www.mylab.com (192.168.1.5)
- Guest PCs cannot reach Staff devices (100% packet loss, ACL deny matches confirmed with `show access-lists`)
- Guest PCs can still reach their own gateway

## Skills demonstrated
Subnetting, inter-network routing, VLANs, DHCP, DNS, ACLs, switch port security, troubleshooting with ping, ipconfig, and show commands.

## Files
- `Segmented-Network-Lab.pkt`: open with Cisco Packet Tracer
- Screenshots of topology and test results
