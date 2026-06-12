---
title: "[SOLVED] Java cant seem to connect to certain websites when host in static?"
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by Deery50 on 2013-06-16
I am required for the sake of my home server to keep my server computer on the same static inet address so that I don't have to change the ports around every time the address changes. Because of this my /etc/network/interfaces file is as follows:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1

```

This works fine but the problem now is that Java can't connect to any websites within my server's console to check or download anything. It only works if I keep interfaces with it's default dhcp value (and yes I have tested this many times). This is how it has to be to make it able to connect:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp
# iface eth0 inet static
# address 192.168.1.105
# netmask 255.255.255.0
# gateway 192.168.1.1

```
Would there be anyway to get java able to connect to any websites while still having a static inet address? Thanks to anyone that helps. For your responses, know that I am ok at technology and using Ubuntuserver but that I am new to this field of things.

Edit: Just as an example to the kind of errors I get in my server, these are the types of messages that come up (this is a minecraft bukkit server):
```

ava.lang.RuntimeException: java.net.UnknownHostException: dev.bukkit.org
    at com.drtshock.obsidiandestroyer.Updater.read(Updater.java:622)
    at com.drtshock.obsidiandestroyer.Updater.readFeed(Updater.java:571)
    at com.drtshock.obsidiandestroyer.Updater.<init>(Updater.java:203)
    at com.drtshock.obsidiandestroyer.ObsidianDestroyer.onEnable(ObsidianDestroyer.java:52)
    at org.bukkit.plugin.java.JavaPlugin.setEnabled(JavaPlugin.java:217)
    at org.bukkit.plugin.java.JavaPluginLoader.enablePlugin(JavaPluginLoader.java:457)
    at org.bukkit.plugin.SimplePluginManager.enablePlugin(SimplePluginManager.java:381)
    at org.bukkit.craftbukkit.v1_5_R3.CraftServer.loadPlugin(CraftServer.java:282)
    at org.bukkit.craftbukkit.v1_5_R3.CraftServer.enablePlugins(CraftServer.java:264)
    at net.minecraft.server.v1_5_R3.MinecraftServer.j(MinecraftServer.java:304)
    at net.minecraft.server.v1_5_R3.MinecraftServer.e(MinecraftServer.java:283)
    at net.minecraft.server.v1_5_R3.MinecraftServer.a(MinecraftServer.java:243)
    at net.minecraft.server.v1_5_R3.DedicatedServer.init(DedicatedServer.java:151)
    at net.minecraft.server.v1_5_R3.MinecraftServer.run(MinecraftServer.java:382)
    at net.minecraft.server.v1_5_R3.ThreadServerApplication.run(SourceFile:573)
Caused by: java.net.UnknownHostException: dev.bukkit.org
    at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:178)
    at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:391)
    at java.net.Socket.connect(Socket.java:579)
    at java.net.Socket.connect(Socket.java:528)
    at sun.net.NetworkClient.doConnect(NetworkClient.java:180)
    at sun.net.www.http.HttpClient.openServer(HttpClient.java:378)
    at sun.net.www.http.HttpClient.openServer(HttpClient.java:473)
    at sun.net.www.http.HttpClient.<init>(HttpClient.java:203)
    at sun.net.www.http.HttpClient.New(HttpClient.java:290)
    at sun.net.www.http.HttpClient.New(HttpClient.java:306)
    at sun.net.www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:995)
    at sun.net.www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:931)
    at sun.net.www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:849)
    at sun.net.www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1299)
    at java.net.URL.openStream(URL.java:1037)
    at com.drtshock.obsidiandestroyer.Updater.read(Updater.java:618)
    ... 14 more

```
Once again, thanks a ton to anyone who responds.

---

### Post by Iowan on 2013-06-16
Have you tried setting up a static lease (reserved address) for the server in your router?

---

### Post by Deery50 on 2013-06-16
> **Iowan said:**
> Have you tried setting up a static lease (reserved address) for the server in your router?
My router currently does not support that, unless I loaded 3rd party firmware (which I guess will be the last option)

---

### Post by Iowan on 2013-06-16
There may be other options - see if routing or DNS server changes between static and DHCP settings.

---

### Post by Deery50 on 2013-06-16
> **Iowan said:**
> There may be other options - see if routing or DNS server changes between static and DHCP settings.
Sorry, I am a bit confused on what you mean. The current configuration I have set in the config is working for a large majority of web-based processes except java.

---

### Post by steeldriver on 2013-06-16
You don't appear to be specifying any DNS servers in your static interface definition - when you use DHCP, it presumably gets that info from your router but for the static config you will need to add a line like

```
dns-nameservers 8.8.8.8 8.8.4.4
```

or whatever are your preferred primary and secondary public nameservers

---

### Post by Deery50 on 2013-06-17
> **steeldriver said:**
> You don't appear to be specifying any DNS servers in your static interface definition - when you use DHCP, it presumably gets that info from your router but for the static config you will need to add a line like

```
dns-nameservers 8.8.8.8 8.8.4.4
```

or whatever are your preferred primary and secondary public nameservers
This fixed everything! Thanks so much!

---

