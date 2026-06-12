---
title: "Intermittent startup problems"
date: 2009-02-15
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-02-15
Most of the time, when I switch my PC on, it boots just fine and goes into the MythTV screen.

Sometimes, however, it gets as far as the Mythbuntu logo with the progress bar underneath it, and when the progress bar has finished, it goes to a blank screen with a flashing cursor top left and just stays there.

Any ideas what might be causing this and how to fix it?

Thanks
NM

---

### Post by scary_jeff on 2009-02-17
When in the error state, have a look through /var/log/syslog by switching to a different PTS (CTRL+ALT+F1/2/3 etc), and see if there are any errors listed. The file is probably quite long, but it should give some clue as to what is going wrong.
If you have a second machine, it might be easier to access the log from it using ssh over the network.

---

### Post by NautiusMaximus on 2009-02-20
Thanks for that. I do have a second machine on the same network (in fact 2 other machines, one running Windows and one running Ubuntu), but as I'm a total Linux newbie I'm afraid I know nothing of this "ssh over the network" of which you speak. Is there some simple documentation of it you could point me to please?

Many thanks
NM

---

### Post by scary_jeff on 2009-02-20
Oh, ok. When you have booted normally, install ssh (sudo apt-get install ssh) on the mythbuntu machine. Then on the laptop, run 'ssh -X <mythbuntu machine user name>@<IP address of mythbuntu machine>' (for example, ssh -X myname@192.168.1.1). It will prompt for the password for the mythbuntu machine, and ask you to accept a security certificate.

The terminal then becomes a terminal as if you were using the mythbuntu machine. You can open the log file using this terminal (nano /var/log/syslog), or if you're lucky, it might work to run 'gedit /var/log/syslog', which is a more user friendly editor.

If you don't know the IP address, open a terminal on the mythbuntu machine, and run ifconfig. If the machine hasn't booted up properly (the problem you're having), press CTRL+ALT+F1, log in with your username and password, and run ifconfig here. The one problem you might have is that depending on where the bootup is stopping, the mythbuntu machine might not have a working network interface when it has failed to fully boot up. In this case, just forget ssh; press CTRL+ALT+F1, log in, and run 'nano /var/log/syslog', then see if there are any obvious errors. You could also look in Xorg.0.log, in the same directory.

---

### Post by NautiusMaximus on 2009-02-21
Many thanks for that.

I've installed ssh, and of course it then booted perfectly so I have yet to try it with it not booting (don't you just love intermittent problems!)

I tried CTRL+ALT+F1 when it had failed to boot, but that didn't seem to do anything.

I do have some more information, however. I left the blinking cursor for a while one time when it was failing to start properly, and after a pause of a few minutes a whole load of text appeared on the screen, mostly stuff saying it was doing something and then saying [OK]. I never see this when it boots normally.

It got as far as a bit that looked like this when it stopped again:

> Starting bluetooth
[389.408984] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CUSUM feature.

Is that useful information in any way?

---

### Post by NautiusMaximus on 2009-02-22
Well, I couldn't SSH to it while it was in the error state. I guess it hasn't got as far as enabling networking?

But perhaps it doesn't matter. I look at the system log you described earlier after it had booted properly, and the events from the failed boot were still in the log file.

Now I'm not used to reading these files and don't really know what I'm doing, but the last few lines before it seemed to grind to a halt were all about Bluetooth. Here they are:

> Feb 22 11:02:30 htpc bluetoothd[7291]: Bluetooth daemon
Feb 22 11:02:30 htpc kernel: [  388.111239] Bluetooth: Core ver 2.13
Feb 22 11:02:30 htpc kernel: [  388.111898] NET: Registered protocol family 31
Feb 22 11:02:30 htpc kernel: [  388.111902] Bluetooth: HCI device and connection manager initialized
Feb 22 11:02:30 htpc kernel: [  388.111906] Bluetooth: HCI socket layer initialized
Feb 22 11:02:30 htpc bluetoothd[7291]: Starting SDP server
Feb 22 11:02:30 htpc kernel: [  388.144913] Bluetooth: L2CAP ver 2.11
Feb 22 11:02:30 htpc kernel: [  388.144919] Bluetooth: L2CAP socket layer initialized
Feb 22 11:02:30 htpc kernel: [  388.183381] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 22 11:02:30 htpc kernel: [  388.183389] Bluetooth: BNEP filters: protocol multicast
Feb 22 11:02:30 htpc kernel: [  388.226480] Bridge firewalling registered
Feb 22 11:02:30 htpc bluetoothd[7291]: bridge pan0 created
Feb 22 11:02:30 htpc kernel: [  388.259977] Bluetooth: SCO (Voice Link) ver 0.6
Feb 22 11:02:30 htpc kernel: [  388.259985] Bluetooth: SCO socket layer initialized
Feb 22 11:02:30 htpc bluetoothd[7291]: Starting experimental netlink support
Feb 22 11:02:30 htpc bluetoothd[7291]: Failed to find Bluetooth netlink family
Feb 22 11:02:30 htpc bluetoothd[7291]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so


There was nothing after that until it logged the restart when I pressed the reset button.

Does that mean that a problem with Bluetooth is stopping the PC from booting? I have no Bluetooth equipment and no intention of using any in the foreseeable future, so can I just disable it so it doesn't even try to do what it's currently trying and failing to do? If so, how?

Many thanks
NM

---

### Post by NautiusMaximus on 2009-03-07
Bump

---

