---
title: "&quot;Device Not Ready (Firmware Missing)&quot;"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by LawrenceLovesLinux on 2011-02-08
Recently, I wiped my existing install of Ubuntu 10.10 and reinstalled it over. That went smoothly, except for one little snag. Now when I try to connect to the Internet, up on the top when I click the little network icon, under Wireless Networks, instead of showing the networks I can connect to, it says:

"Device Not Ready (Firmware Missing)"

So I move the little wireless switch on my laptop, and then it says:

"Wireless Disabled"

What did I do, and how do I fix it? :-k

---

### Post by puppywhacker on 2011-02-09
you are missing the firmware package for your wireless device.

I am missing the information which exact device you have in your laptop

you fix it by installing the drivers either at "propriatory drivers" or in the "software center" and look for firmware or install all package named "firmware-*.deb"

---

### Post by Yogotiss on 2011-03-17
> **LawrenceLovesLinux said:**
> Recently, I wiped my existing install of Ubuntu 10.10 and reinstalled it over. That went smoothly, except for one little snag. Now when I try to connect to the Internet, up on the top when I click the little network icon, under Wireless Networks, instead of showing the networks I can connect to, it says:

"Device Not Ready (Firmware Missing)"

So I move the little wireless switch on my laptop, and then it says:

"Wireless Disabled"

What did I do, and how do I fix it? :-k

Try this out. Open Synaptic and search "b43", then install "firmware-b43-installer" "b43-fwcutter" also "firmware-b43legacy-install". My wireless started working instantly and if it doesn't work as fast for you try restarting after installing those packages and see if that helps.

---

### Post by da808wiz on 2011-05-30
I am running 11.04 and I was struggling with the wifi until I tried the following:

1)  Go to Software-Center and type firmware- (remember to include the dash)
2)  Select firmware-addon-dell, then install
3)  When it's done, reboot.

For me, the WiFi light on my D630 laptop came on immediately upon reboot.

There were a lot of other steps prior to this, as I tried solutions regarding ndiswrapper and downloading the Windows XP driver from Dell's support website for my laptop by looking up my Dell service tag.

So I'm not sure if it was a combination of the firmware-addon-dell and the ndiswrapper solutions hinted to by this link [HOWTO: Dell Inspiron E1505 Wireless (Broadcom 1390 WLAN) - ubuntuforums]("http://ubuntuforums.org/showthread.php?t=297092")

My steps were a little different due to errors with ndiswrapper when installed as specified.

Maybe my issue was unique because I loaded 11.04 64-bit.

My additional steps were to install ndiswrapper etc from the sofware-center by typing ndiswrapper, and ndiswrapper- (remember the trailing dash (-) to install ndiswrapper-source and ndiswrapper-dkms, ndiswrapper-utils-1.9 and ndiswrapper-common are already installed by ndiswrapper no dash)

Good luck and shoot me a question if you need me to explain more clearly.  I'll reply to this thread so all can read...

---

### Post by KingLewy on 2011-06-14
Thanks! "firmware-b43-installer" worked a treat on my parents Acer Aspire boasting 11.04. Life saver.

---

