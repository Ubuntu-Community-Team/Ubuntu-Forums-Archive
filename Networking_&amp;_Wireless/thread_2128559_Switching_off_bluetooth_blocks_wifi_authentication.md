---
title: "Switching off bluetooth blocks wifi authentication in hp laptop"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by catarano on 2013-03-23
I have a touchsmart tm2 1090 laptop with builtin bluetooth and wifi adapter (intel N1000) with Ubuntu 12.10

I cannot switch off bluetooth

If I do that, then the wifi stays on, I can see networks around, but cannot authenticate to my router.

Somehow the authentication does not go through

I get asked on and on the authentication password, but it never logs in

I have no Idea what that could be.

In ubuntu 10.04 I could switch off bluetooth, but wlan kept on working properly.

Since later releases I cannot do that anymore.

---

### Post by matt_symes on 2013-03-23
Hi

Enable bluetooth so you cannot connect to the wifi network, open a terminal and type

```
sudo service bluetooth stop
```

Does this disconnect you from the network ? Can you still connect to the network ?

Start bluetooth again using

```
sudo service bluetooth start
```

When you cannot connect to the wifi network, open a terminal and type

```
sudo rfkill list all
```

Post the results back here.

You may have to install rfkill with

```
sudo apt-get install rfkill
```

Kind regards

---

### Post by catarano on 2013-03-23
this is what happens

```
~ $ sudo service bluetooth stop
bluetooth stop/waiting

```

still the bluetooth applet is lightened up, like bluetooth is still on
but, if I open the bluetooth settings from gnome control center, bluetooth is shown to be off
in this situation the network works normally
if in this situation I test with rfkill I get

```
~ $ rfkill list all
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

so from rfkill point of view, bluetooth is still on

however, if I do 
```
~ $ rfkill block 4 && rfkill list all
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

the bluetooth applet gets dimmed and it reports that bluetooth is off, as well as in control settings
in this situation the network works

instead, if I switch off bluetooth directly from the applet or I do
```
rfkill block 3
```

the wifi led blinks for a while, then it goes to white, like wifi is supposed to be on and I get the authentication problem mentioned in the first post
and the network does not work.

so the question is if bluetooth is really off when I give rfkill to block hci0

after stopping the service and blocking hci0 I tried to launch blueman and got the following

> Bluez daemon is not running, blueman-manager cannot continue.
This probably means that there were no Bluetooth adapters detected or Bluetooth daemon was not started.

so it seems to have worked
also because if I scan around for bluetooth devices with my smartphone I cannot detect my laptop

it seems however, for my laptop, the bluetooth applet switches off the wrong device
should I file a bug for it?
another option would be to have a script that blocks hci0 at startup, the problem is that with rfkill devices change continuously number....:-( 

Thanks a lot

---

### Post by matt_symes on 2013-03-24
Hi

> so from rfkill point of view, bluetooth is still on

If you stop the Bluetooth daemon then Bluetooth is not running even if it is not soft blocked by using rfkill.

> so from rfkill point of view, bluetooth is still on

You can disble wifi networking without blocking wifi using rfkill. The same is true of Bluetooth.

> instead, if I switch off bluetooth directly from the applet or I do...

Hmm. Disabling Bluetooth should not disable wifi i don't think. It certainly does not do that on my laptop.

However, my laptop is not a HP lappy and does not use an vendor specific kernel module for wifi and Bluetooth like yours does.

If you unload the HP kernel module (i assume it's using a HP specific kernel module) do you still get wifi and Bluetooth access and, if you disable Bluetooth, do you still get wifi access ?

Also can you post the output of

```
cat /proc/cmdline
```

and

```
lsmod | grep hp
```

Kind regards

---

