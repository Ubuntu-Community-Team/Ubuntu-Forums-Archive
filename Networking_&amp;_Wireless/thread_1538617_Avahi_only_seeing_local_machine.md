---
title: "Avahi only seeing local machine"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by tube013 on 2010-07-25
Hi,

I have a few ubuntu machines in my house, 1 mythtv backend server with other services as well, 2 mythbuntu frontends boxes hooked up to tv's etc.  I wanted to push the audio from my laptop out over pulseaudio to the machine connected to the AV equipment.

I could not see any other pulseaudio sinks in padevchooser... this lead me down the road to investigating avahi.

When I run avahi-browse on my laptop (hydrogen) it only returns the services published from itself:


```
$ avahi-browse -ta
+ wlan0 IPv4 byron's remote desktop on hydrogen            VNC Remote Access    local
+ wlan0 IPv4 hydrogen [00:1b:77:71:97:76]                  Workstation          local
```

if I run the same on my mythbuntu machine (both machines are running 10.04)
```
$ avahi-browse -ta
+ eth0 IPv4 Series 3                                      _tivo-videos._tcp    local
+ eth0 IPv4 byron@myth-mini: Internal Audio Digital Stereo (IEC958) PulseAudio Sound Sink local
+ eth0 IPv4 byron@myth-mini                               PulseAudio Sound Server local
+ eth0 IPv4 hydrogen [00:1b:77:71:97:76]                  Workstation          local
+ eth0 IPv4 fluffhead [00:12:f0:74:a9:92]                 Workstation          local
+ eth0 IPv4 myth-mini [00:16:cb:a8:30:ec]                 Workstation          local
+ eth0 IPv4 mythtv [00:1c:c0:37:40:c8]                    Workstation          local
+ eth0 IPv4 byron's remote desktop on hydrogen            VNC Remote Access    local
+ eth0 IPv4 byron's remote desktop on mythtv              VNC Remote Access    local
+ eth0 IPv4 1106 Media Vault                              iTunes Audio Access  local
+ eth0 IPv4 1106 Media Vault                              Web Site             local
+ eth0 IPv4 1106 Media Vault                              _rsp._tcp            local
+ eth0 IPv4 Series 3                                      _tivo-remote._tcp    local
+ eth0 IPv4 Series 3                                      Web Site             local
+ eth0 IPv4 myth-mini Remote Input                        _rinput._tcp         local

```

My laptop has vmware on it, and I've changed the vmnet intefaces to not support multicast so avahi ignores them.  but I'm still at a loss to why my laptop can't see the other machines on my network with avahi (mdns).

---

### Post by tube013 on 2010-07-25
Well.. I'm still baffled, but I connected to a secondary wireless access point, not the built in AP in the Verizon Fios router (which is still handling dhcp) and now avahi is seeing the all the devices on my network.

---

