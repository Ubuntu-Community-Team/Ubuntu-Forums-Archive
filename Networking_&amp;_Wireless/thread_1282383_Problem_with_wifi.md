---
title: "Problem with wifi"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by DBoulay on 2009-10-04
Hi. I just bought a Dell Vostro A90 netbook equipped with Ubuntu, and I'm unable to connect to my wifi network (D-Link DIR-615). I can detect the network and enter a password, but the password never seems to work; it's not flat-out refused, but my computer tries to connect for a short time and then asks me for the password again.

I've tried to follow the troubleshooting guide that came with the netbook, but it stops working at step 2. When I input the command "sudo lshw -C network" into the terminal, I am asked for my admin password. I type in the password, aware that nothing will actually be displayed, and the return I get is "command not found." Any subsequent tries immediately give the same result without asking for a password.

I confess that I am a total Ubuntu novice, and I hope I haven't asked a question whose answer I could have easily found elsewhere. But frankly, I'm at the end of my wits and am even considering returning the netbook. Any help would be greatly appreciated.

Thanks.

---

### Post by freechiru on 2009-10-04
If it's any consolation, I've been having exactly the same problems, and I think it's quite common.  (Mine still aren't fixed.)  Do you know what kind of wireless card you have?  Apparently this is immensely useful to know.  lspci -vv is the code you need to use to find out; on my computer, it was the last entry that code produced.

Have a look around; there are plenty of threads similar to this on this forum.  One of them might have a solution that will work for you.

---

### Post by DBoulay on 2009-10-04
I believe my card (network controller?) is a Broadcom Corporation BCM4312 802.11b/g. Does that help? I've browsed the forum and still can't figure out what's going on. I'm not a techie, so a lot of this stuff is incomprehensible to me.

---

### Post by houstonbofh on 2009-10-04
> **DBoulay said:**
> I believe my card (network controller?) is a Broadcom Corporation BCM4312 802.11b/g. Does that help? I've browsed the forum and still can't figure out what's going on. I'm not a techie, so a lot of this stuff is incomprehensible to me.
You need the firmware.  Plug in an enthernet cable so you have internet.  Run the System --> Administration --> Hardware Drivers application and activate the driver (which installs b43-fwcutter) and it will work.

---

### Post by DBoulay on 2009-10-05
I reinstalled my router so that I no longer have to input a password and now it works. However, I'm fairly certain that the same problem will persist on any network that is protected by a password. I ran the Hardware Drivers application, and there is only one driver in the list; it is labelled "wl" and is already enabled.

---

### Post by tjutberg on 2009-10-08
I have the same, or a similar, problem on my Asus A6R.
After installing the drivers for the broadcom wireless card i can detect the network but not connect to it. I then disabled the WPA/PSK on the router and i could connect immediately with no problems but with the security enabled i won't work.

I don't know if this has anything to do with it but when I'm typing in the password in the network-tool and click 'apply' and after that use the "show password" function i see a very long string of random numbers and letters, not the password i typed.

Im running a fresh install of ubuntu 9.04.
thanks

---

### Post by houstonbofh on 2009-10-09
I believe the firmware only supports WEP.

---

### Post by tjutberg on 2009-10-15
> **houstonbofh said:**
> I believe the firmware only supports WEP.
do you know if wpa/psk-support is planned for any time soon?
thx anyway, i'll go for wep then.

---

