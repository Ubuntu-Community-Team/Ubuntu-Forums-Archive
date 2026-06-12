---
title: "New Dell Vostro 2520 with 12.10; wireless (BCM43142) not working"
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2012-12-13
[B]Edit for people finding this thread from Google/Search:

Here's what worked for me:[/B]

```
sudo apt-get install linux-headers-generic build-essential dkms

```

Then:

```
cd Desktop   <--or wherever you downloaded the deb
    sudo dpkg -i wire*.deb
    sudo modprobe wl
```

Good luck!

----Start original post----

I've done a fair bit of googling and since this is a new laptop with no data saved to it yet I went ahead and just tried to reinstall a few times after trying a few "solutions" on AskUbuntu, none of which ever worked for various reasons.  One of them involved installing the build-essential package and downloading a deb file from someone's dropbox.  The result I got out of that (after examining a log file) said something like a folder it was looking for (during the build process) didn't exist.  Another solution involved reinstalling the... f-cutter package (sorry, I don't remember exactly what but I'm sure most here know what that's about).  Anyway that didn't work either.

So right now I am running Ubuntu 12.10 (uname -a output: Linux Vostro-2520 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux).  Using my android as an external wireless adapter I connected to the internet before installing and applied updates during as well as after install.  As of right now there are no more updates available.  (Edit:  Just to be clear, I have installed nothing else nor attempted anything new to try and get this adapter fixed yet and await the first suggestions I see here instead).

Also, if I go into Software Sources and look under the Additional Drivers tab it does not list any proprietary drivers either in use or available to be enabled; it's empty.

Relevant output from lspci -nn:

```
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

```

Output of iwconfig:

```
usb0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

```

rfkill list all:

```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

Anyway, it's my dads and I'll be seeing him on Saturday so I've got some time to work with this and hopefully get feedback from y'all on any problems I encounter on suggestions about getting this puppy up and running.  Thanks in advanced.

---

### Post by chili555 on 2012-12-13
> Broadcom Corporation BCM43142 802.11b/g/n [[COLOR="Red"]14e4:4365[/COLOR]] Please see here: [http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923](http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923)

Note well:> I am not sure it is even possible in a 32-bit system.And, of course, this!> Awesome, that worked! 

---

### Post by diablo75 on 2012-12-13
This did the trick.  I believe the key difference here in these instructions as opposed to other solutions I came across on AskUbuntu is the inclusion of the dkms package, which I don't recall seeing posted elsewhere.  It might also be possible that the deb file included is different than the one I was downloading earlier.  What I can happily say is this did the trick perfectly!  Thank you very much!!

---

### Post by chili555 on 2012-12-13
> **diablo75 said:**
> This did the trick.  I believe the key difference here in these instructions as opposed to other solutions I came across on AskUbuntu is the inclusion of the dkms package, which I don't recall seeing posted elsewhere.  It might also be possible that the deb file included is different than the one I was downloading earlier.  What I can happily say is this did the trick perfectly!  Thank you very much!!All exactly true. You'd almost think someone went to the trouble to install it on a 64-bit 12.10 system without error before they wrote the instructions. 

Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by Naveen Goud on 2013-03-07
Hi I have tried all the above things but there is still issue in wireless.It still says no properietary drivers found... Kindly suggest on what needs to be done to resolve this issue

---

### Post by chili555 on 2013-03-07
> **Naveen Goud said:**
> Hi I have tried all the above things but there is still issue in wireless.It still says no properietary drivers found... Kindly suggest on what needs to be done to resolve this issueDo you have exactly the same device?```
lspci -nn | grep 0280
```Is yours a 64-bit system?```
arch
```Is there any error when you load the driver?```
sudo modprobe wl
```Are these the instructions you followed?> Please verify your pci.id with a terminal command:

    lspci -nn

Is it 14e4:4365? I am not sure it is even possible in a 32-bit system. If you have a 64-bit system and the device I mentioned, then I suggest this package: [http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb](http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb)

First install the prerequisites:

    ```
sudo apt-get install linux-headers-generic build-essential dkms
```

Then install the package with:

    ```
cd Desktop   <--or wherever you downloaded the deb
sudo dpkg -i wire*.deb
sudo modprobe wl
```


---

