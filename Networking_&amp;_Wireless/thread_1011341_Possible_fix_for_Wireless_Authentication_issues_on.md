---
title: "Possible fix for Wireless Authentication issues on Intrepid"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by Reiger on 2008-12-14
Small 'pointer' compiled from the various tidbits which I came across on these forums (and the internet in general) while troubleshooting my own problems. This pointer may be of help in case your portion of wireless toil & trouble matches (any of) the following symptoms:
[list="1"]
[*]you can't connect to your wireless network even though you do have a working wireless card/usb device with functioning drive;
[*]you can connect sometimes, but most of the time you can't;
[*]you can connect to the Internet but resolving DNS queries (looking up internet addresses) takes exceedingly much time. So much perhaps that you may be connected to the internet yet can't browse it using your browser.
[/list]

This 'fix' assumes a couple of things:
(a) You have a working driver for your Wireless Client card/usb device.
(b) Your device can 'see' the access point (AP), modem/router you want to connect to.

Check by typing:
```

sudo iwlist scan

```

At least *one* 'cell' should be reported, among the cells that are reported should be your Modem/Router/AP. ESSID will tell you which cell is which.

And finally, and most importantly (because this is where Intrepid is likely to give you trouble) your AP of choice uses the IPv4 protocol instead of IPv6. For some reason Intrepid does not [always] correctly detect which protocol to use in a timely manner.

This may manifest itself in a log entry (on your AP) like this if you had assigned a preferred/static IP address to your device:
```

[Time stamp] **UDP Flood to Host** [Your IP], 47573->> [DNS server IP], 53 (from ATM1 Outbound)

```

More importantly you can check if you have reason to suspect IPv6 / IPv4 compatibility issues on your end by looking at the (a) the type of IP addresses given in log entries, and (b) the type of IP addresses your router will let you assign to specific devices. This check boils down to: hexadecimal containing colons? -> IPv6; decimal containing 4 numbers and 3 dots? -> IPv4. Of course if you do not own the AP you can't check; however you can ask your system administrator[s].

This fix (from: [http://ralph.n3rds.net/index.php?/archives/177-How-to-Disable-IPV6-in-Ubuntu.html](http://ralph.n3rds.net/index.php?/archives/177-How-to-Disable-IPV6-in-Ubuntu.html)) does the trick:
Step 1: open the tex file of choice
```

sudo [console_text_editor_here (nano/vim/...)] /etc/modprobe.d/aliases

```
Or (sudo + GUI editor doesn't always work 100% properly, with sudo editing will work but you **might** get the odd file-ownership/permission warning): 
```

gksu [GUI_text_editor_here (gedit/kate/...)] /etc/modprobe.d/aliases

```

Step 2: fixing it
Change the following line:
```

alias net-pf-10 ipv6

```

To:
```

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
# alias net-pf-10 ipv6

```

Step 3: save the file & exit the editor.

Step 4: reboot:
```

sudo reboot

```

Verify that you are now able to access your wireless network.

NOTE: People who use WPA1/WPA2 PSK authentication methods should not use the network-manager package as network-manager does not seem to support WPA-PSK authentication. You can use [WCID]("http://wicd.sourceforge.net/") instead, which (verifiably) does play by the rules. With WPA-PSK the client isn't supposed to (re)hash the network-password but with WPA it is because passwords are *directly* used to generate encryption keys. You can see the issue here: network-manager *does* (re)hash the password.

---

### Post by Aearenda on 2008-12-14
I just wanted to say that contrary to your note at the end, Network Manager has been working fine for me with WPA-PSK for several releases now, with D-Link and Belkin access points. It works in Intrepid, but it's a bit slower than Hardy to associate the first time with a new network. I have ipv6 disabled anyway as described here. I'm commenting simply because I wouldn't want to give people the idea that they HAD to go to WiCD to make WPA-PSK work, or that NM never works. It does, for me at least.

---

