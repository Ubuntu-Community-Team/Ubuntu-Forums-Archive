---
title: "Ping Portable Ubuntu from Windows"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by nottrobin on 2009-04-11
This is a question about "[Portable Ubuntu for Windows]("http://portableubuntu.demonccc.com.ar/")" (hereafter "Pubuntu") - Ubuntu 8.04 LTS, running *natively* within (in this case) Windows XP SP3. It would help if you know something about Pubuntu, but I imagine you Ubuntu geniuses could probably help anyway.

I extracted Pubuntu straight and haven't made any changes, so it's still on its default setup.

Pubuntu can access the internet fine through my Windows connection.

I can also ping "192.168.0.2" (my windows IP address) and "192.168.0.1" (my network gateway) from within Pubuntu terminal, but, strangely, not "google.com". Even though "lynx http://www.google.com" takes me to the Google home-page absolutely fine.

My Pubuntu ifconfig returns the following:

```

eth0      Link encap:Ethernet  HWaddr 00:ff:75:39:d3:c1  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2ff:75ff:fe39:d3c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4392571 (4.1 MB)  TX bytes:32524940 (31.0 MB)
          Interrupt:2

```

My problem, and what I'd like to fix, is that Windows can't ping Pubuntu. If I ping 10.0.2.15 from Windows, I get "request timed out".

I tried changing Pubuntu's IP address to within the 192.168.0.* range - it crashed Pubuntu. I tried adding a second interface at eth0:1, but it didn't help.

Does anyone have any ideas?

Ta,
Robin.

---

### Post by nottrobin on 2009-04-12
After a lot of work I have now solved this - I successfully created a network bridge between Pubuntu and Windows, so Windows can now ping Pubuntu.

Here's how I did it:

1) If you don't have it already, download and extract [Portable Ubuntu for Windows]("http://portableubuntu.demonccc.com.ar/").

2) Download and install [WinPcap]("http://www.winpcap.org/") - this is essential for the network bridge to work.

3) Download the [colinux binary executable]("http://sourceforge.net/project/showfiles.php?group_id=98788").

4) Open the executable with an archive manager (e.g. [7-zip]("http://www.7-zip.org/")) and extract "colinux-bridged-net-daemon.exe" into your Portable Ubuntu directory.

5) Open up "[Portable Ubuntu]\config\portable_ubuntu.conf" and add the following line (assuming your local area connection is called "Local Area Connection"):
```
eth1=pcap-bridge,"Local Area Connection"
```

6) Start portable ubuntu (by running "[Portable Ubuntu]\run_portable_ubuntu.bat")

7) When Portable Ubuntu has loaded, open a terminal and type:
```

# sudo echo -e "\n\nauto eth1\niface eth1 inet dhcp\n\n" >> /etc/network/interfaces
# sudo /etc/init.d/networking restart

```
(sudo password is 123456)

8) That's it! Portable Ubuntu should now be connected to your local network. If you type "ifconfig" you should be able to see eth1 has now been assigned a local IP address, and you should be able to ping that IP address from Windows.

:)

Robin.

----

P.s. The point of doing this for me, in case you were wondering, was so I can run a development web-server in Pubuntu and be able to access it from IE7 in Windows (for testing).

---

### Post by juancarlospaco on 2009-04-12
*Sometimes ping goes, but dont go back...*

---

### Post by boxmonkey on 2009-04-16
After following these instructions pubuntu lost the ability to initiate connections with the outside world (i.e. could not ping google, apt-get did not work...), because it was choosing the default gateway for eth0 even though the internet connection lived on eth1.

At first I tried hard coding the route but that's not very portable, is it?

I found a much simpler fix: swap eth0 and eth1 in portable_ubuntu.conf

Now my config looks like this:

```
kernel=vmlinux
cobd0=images\rootfs.img
cobd3="D:\Documents and Settings\czw5hv\Application Data\Windux\images\root.img"
cofs0=config
cofs1=c:\ #Para tener acceso a la unidad C:
#cofs1=otra_unidad:\ #Si se necesita tener acceso a otras unidades… ej: d:\
#scsi0=cdrom,\Device\Cdrom0 # Para tener acceso al CDROM de la PC
root=/dev/cobd0
ro
initrd=initrd.gz
mem=256
eth1=slirp,00:ff:75:39:D3:C1,tcp:22:22
eth0=pcap-bridge,"Local Area Connection"
exec0="Xming\Xming.exe :0 -notrayicon +bs -wm -auth Xauthority -clipboard -multiwindow -dpi 100"
exec1=pulseaudio-0.9.6\pulseaudio.exe # Ejecuta al servidor Pulse Audio para Windows
```

And everything is happy.

---

### Post by nottrobin on 2009-04-16
Interesting that I didn't have the same problem. Ubuntu seems to juggle the two connections perfectly happily.

Any ideas why? Because I'm trying to tweak and repackage Portable Ubuntu as a [PortableApp]("http://portableapps.com/about/what_is_a_portable_app"):

[Ubuntu for Windows PortableApp]("http://www.robinwinslow.co.uk/projects/ubuntuforwindows-portableapp/")

---

### Post by demonccc on 2009-04-27
Hi, how are you?

Also, you can configure Pubuntu to use slirp instead WinPcap to connect from your Windows machine.

You need add the application port that you need use from Pubuntu.

Pubuntu has configure the port 22 to connect by ssh from Windows or other machines that are in the same net that your PC.
```

eth0=slirp,00:ff:75:39:D3:C1,**tcp:22:22**
```

If you need, for example use Apache from Pubuntu, you need install Apache in Pubuntu and change the above line to:

```
eth1=slirp,00:ff:75:39:D3:C1,tcp:22:22**/tcp:80:80**
```

Now, you can access form Windows to Apache that are installed in Pubuntu. Also, if you try access to the port 80 of your PC from other machine , Apache will respond also.

---

