---
title: "Realtek chipset RTL8187L Alfa AWUS036H Ubuntu 10.04 Working"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by otriades on 2010-10-25
I use Ubuntu 10.04 with an Alfa Network AWUS036H USB wireless adaptor with a Realtek chipset RTL8187L.

With this procedure, everything will work perfect !

1) Download [SIZE=4][COLOR=Red]**THIS**[/COLOR][/SIZE] driver (previous version didn't work for me):

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L)

or (this is the same file):

[http://www.4shared.com/file/BSepYhR2/rtl8187L_linux_26104008202010r.html](http://www.4shared.com/file/BSepYhR2/rtl8187L_linux_26104008202010r.html)

2) Extract

3) Open a terminal window, go to where you extracted.

4) run:
sudo make

5) run:
sudo make install

6) reboot

In my case, when the network manager applet said "connected" I have to wait about a minute to start browsing the web.

Everything works pefect, never disconnect, etc.

---

### Post by zapho on 2010-12-12
Hi otriades,

I'm using the same wifi adaptor and had trouble using it with ubuntu 9.10. Since updating to 10.04 a while ago, the adaptor worked out of the box, no need to install additional drivers. 

However, its not working 100% perfectly. It occasionally disconnects (like, once every few hours) and requires me to manually reconnect it. This isn't much a of problem when I'm sitting at the computer, but is very annoying if I want to access it remotely. Also, it tends to disconnect more often if I try heavy usage, like copying large files via samba etc. 

What I'm wondering is, do these new drivers fix this problem?

Thanks!

---

### Post by petrus66 on 2011-02-01
Are you sure that you not have to blacklist anything?
I get kernel panic of some kind and Ubuntu hangs on a black screen.

2.6.32-28-generic is running and the adaptor is the same.

I really messed up with this first:
[URL="http://forum.aircrack-ng.org/index.php?topic=5755.msg30696#msg30696"]TUTORIAL: Installing driver RTL8187, r8187, rt2800usb on Ubuntu Jaunty and Lucid
[/URL]
Only a kernel update that happened to come across, saved me from all the trouble to get it all back to the state that it was before with the original RTL8187L driver.
That will say to a state where the signal is lower than 70%, surfing is most of the time impossible.

Then I tried with ndiswrapper but that did not work either so I uninstalled it with synaptic and deleted the blacklist that it had created. Now I know that pointing out the driver .ini directly from the installation CD was the mistake I did.

The laptop uses also internal atheros ar2413 nic and I loose the connected Alfa too when I try to disable the internal wifi with the hardware disable button.

Any ideas?

I probably try with the ndiswrapper again or have to reinstall windows on the side of Ubuntu just for surfing with Alfa and maybe for some other stuff like updating some firmware on my phone and gps.

---

### Post by walt.smith1960 on 2011-02-01
Yes the hardware switch kills ALL network adapters on my Thinkpad R61.  The way I disabled my internal adapter was to look through DMESG to find the module that powered the internal adapter and blacklist that module.

---

### Post by ~zenr on 2011-02-06
> **walt.smith1960 said:**
> Yes the hardware switch kills ALL network adapters on my Thinkpad R61.  The way I disabled my internal adapter was to look through DMESG to find the module that powered the internal adapter and blacklist that module.

Hi walt.smith1960,

Your using 10.10 now, may I know if you installed the RT8187L Alfa usb wireless successfully? Can you please post the details, thanks!

---

### Post by walt.smith1960 on 2011-02-08
> **~zenr said:**
> Hi walt.smith1960,

Your using 10.10 now, may I know if you installed the RT8187L Alfa usb wireless successfully? Can you please post the details, thanks!

Sorry, I am not using a device with an RTL8187L chipset,  I was explaining how I disabled an installed PCIe adapter, in my case an Intel 3954abg(?).

---

### Post by Micro-soft_WIn_Dos_SuCkS on 2011-09-15
Thanks for this, I was using the original driver, but it tend to be slow when browsing and to disconect even if said it was connected. I even installed several versions of UBUNTU Linux just to fix this and in UBUNTU Linux 10.04 LTS, I tried that driver you post and work well, no ndiswrapper (which I did and didnt work well either). 

Thanks, now no disconnects, errors or latency errors :)

fr33
Joey

---

### Post by timeshare on 2011-10-01
[http://www.alfanete.eu/en/alfa-awus036nhr.html](http://www.alfanete.eu/en/alfa-awus036nhr.html) Can I use this, have someone tested it?

---

### Post by SpindizZzy on 2011-10-02
Ok, so I'm stuck ...:(

I'm trying to install my newly-bought Alfa UBDo-n Outdoor Long-Range antenna on  Ubuntu 10.04 (Lucid), Kernel 2.6.39.4.

I used the CD that came with it (package called '2009_1110_RT3070_Linux_STA_v2.1.2.0').

In the terminal i get this:

[I]sudo make install
make -C /root/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/root/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /root/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.39.4/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.39.4/kernel/drivers/net/wireless/
install: cannot stat `rt3070sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/root/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'
make: *** [install] Error 2[/I]


Why is this ?? I tried following the steps as described above... I did search for other (newer ??) versions of this driver-software, but i got the same problem.

All help appreciated !!

Thx in advance & GrtZ from Belgium :):D

---

