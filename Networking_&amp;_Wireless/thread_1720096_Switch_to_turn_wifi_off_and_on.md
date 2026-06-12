---
title: "Switch to turn wifi off and on"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by Longstreet on 2011-04-02
I searched for this, and all I saw was advice on how to make wifi work. Mine works just fine, I'm looking for a way to turn it off to save battery life.

Here's what I mean. Aspire One D255, Fn F3 toggles wifi off and on, with an indicator light and, in Win 7, an on-screen indicator. Fn F3 doesn't work in Ubuntu, and there are times I'd like to turn the wifi off. Is there a command to do this? Or maybe something in the menus that I'm missing?

---

### Post by moejay on 2011-04-02
I don't know if you can turn it off more than by typing
 'ifconfig wlan0 down' or whatever your interface is,  in the terminal
and to bring it up 'ifconfig wlan0 up'

---

### Post by Longstreet on 2011-04-02
> **moejay said:**
> I don't know if you can turn it off more than by typing
 'ifconfig wlan0 down' or whatever your interface is,  in the terminal
and to bring it up 'ifconfig wlan0 up'

Okay. I figured there'd be something in terminal. I'll give it a try. Thank you!

---

### Post by mads65 on 2011-04-02
Hi!

If you run 'sudo iwconfig' now, and look at the output for your wireless interface, you should see:
```
Power Management:off
```

**To turn it on:**

Edit /etc/rc.local (gksudo gedit /etc/rc.local)

and add this line '/sbin/iwconfig wlan0 power on'

almost at the end of the file (above 'exit 0'), like this:
```
/sbin/iwconfig wlan0 power on

exit 0
```Save the file. Next time you reboot/turn on your computer, the power management will be loaded.
You can check it by rerunning 'sudo iwconfig'. This time the output should show:
```
Power Management:on
```

---

### Post by Longstreet on 2011-04-04
[QUOTE=mads65;10631093]Hi!

If you run 'sudo iwconfig' now, and look at the output for your wireless interface, you should see:
```
Power Management:off
```


Hmm. Tried it, and this is what I got from 'iwconfig'

joedan@joedan-AOD255E:~$ sudo iwconfig
[sudo] password for joedan: 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  ESSID:"Shelton wifi"  
          Mode:Managed  Frequency:2.467 GHz  Access Point: 00:14:BF:0B:3D:B6   
          Bit Rate=11 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-43 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


What does "All packets received" mean? Do I have the means to do this already, and I just need to find out where and how?

The frowny faces are colons  btw. Not sure what happened there.

---

### Post by mads65 on 2011-04-04
Sorry, I thought power management was off. When you see
Power Managementmode:All packets received
it means that it is set to "all" (receive all packets)

These are the parameters one can add to the command "sudo iwconfig wlan0 power"
(or add to "/sbin/iwconfig wlan0 power" that is added to /etc/rc.local)
off and on -  disable/enable power management
all - receive all packets
unicast - receive unicast packets only, discard multicast and broadcast
multicast - receive multicast and broadcast only, discard unicast packets

---

