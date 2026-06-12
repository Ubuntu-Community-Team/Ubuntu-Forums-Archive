---
title: "help a n00b - new install - wireless not working"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by joehall on 2009-06-27
I have a laptop that's a few years old that I don't use that much any more so I wanted to put Ubuntu on it. The cd/dvd drive is broken so I installed Ubuntu on a USB stick via UnetBootin. I got Ubuntu installed just fine, but I am having a hard time getting it to recognize my wireless card. After a bit of searching I see this is a common issue. Everyone, recommends verifying that my network card's driver is installed. However, I failed to make a note of which card I have before formatting my hard drive. It seems like if I can discover the card installed all I need to do is run a few commands to install it. Is there anyway I can identify the card with out actually opening up the machine to see it?

Please be aware that I am a Linux noob but willing to learn to use the command line & hack a solution if needed. And, that the cd/dvd drive is broken and there is no connection to the web.

---

### Post by Ayuthia on 2009-06-27
We need to figure out which wireless card you have.  You will need to go into the Terminal and do the following:
```
lspci -nn
```and look for the Ethernet Controller or Network Controller entries.  From there, you can let us know which wireless card you have.

You can also check and see if System->Administration->Hardware Drivers hase something there for your wireless card.  That might also be all you need to get it to work.

---

### Post by joehall on 2009-06-27
thank you for your reply. It appears there is a Broadcom B43. I tried Activating the driver by clicking "Activate" in the hardware drivers section under system>administration>hardware drivers. However, when doing this it attempts to download the driver, and this obviously doesn't work because there isn't any connection to the web.

Is there a way I can get this offline myself put it on my USB stick through my windows machine and then install it through that?

---

### Post by philcamlin on 2009-06-27
do you have an ethernet port? :popcorn:

---

### Post by Ayuthia on 2009-06-27
There is a way to do it offline.  However, if you have a 4311, 4312, 4321, 4322, or 4328 card, you should be able to activate the card without having to download anything.  Do you know which model number it was?

Here is a guide for downloading the files to get the b43 module running:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by joehall on 2009-06-27
it appears from the terminal command you gave me earlier, its 4318. I will check out that link you gave me right now.

---

### Post by joehall on 2009-06-27
The link you suggested required either a internet connection or a CD. The CD drive is broken and I obviously can't connect to the internet.

---

### Post by Ayuthia on 2009-06-27
Try this one:
[http://ubuntuforums.org/showpost.php?p=7528709&postcount=33](http://ubuntuforums.org/showpost.php?p=7528709&postcount=33)

The person in that post is in a similar situation.

---

### Post by joehall on 2009-06-27
Ok i have downloaded the tar and moved it over with my USB and placed it on my desktop. When running the first command I get Cannot open: No such file or directory. Is xvjf supposed to apply to a specific directory that the tar file should be in?

---

### Post by joehall on 2009-06-27
ok, i went ahead and typed out the full file path /home/joe/Desktop/b43.tar.bz2 and I got Old option 'b' requires an argument.

---

### Post by Ayuthia on 2009-06-27
It sounds like you added a b in the options list.  The xvjf if just the options for tar.  It stands for eXtract, Verbose, bzip2, and file.  You should just be able to extract the file by doing:
```
cd ~/Desktop
tar xvjf b43.tar.bz2
sudo cp -a b43 /lib/firmware
sudo modprobe -r b43 b44 ssb
sudo modprobe b43
sudo modprobe b44
sudo iwlist scan
```

---

### Post by joehall on 2009-06-27
Ok, that worked, however the last command returned:

```

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan      No scan results.

```

I am assuming that is a failure?

---

### Post by Ayuthia on 2009-06-27
Can you check and see if any messages show up for:
```
dmesg|grep b43
```
We are looking for anything like hardware is off, something is down, or anything with the word error in it.

---

### Post by joehall on 2009-06-27
Everything is on, except I do see

```

Radio hardware status changed to DISABLED

```

And then it says later down

```

The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

```

Could it be the Wireless switch? I tried turning that back on

---

### Post by Ayuthia on 2009-06-27
By any chance, do you have an option in your BIOS to turn on your wireless?  I think that it is a bug because there are a few cards that have this problem where the driver is not able to turn on the card.  However, if you are able to enable the card in the BIOS, it might work.

---

### Post by joehall on 2009-06-27
i just checked bios and the "Wireless LAN" is "Enabled"

---

### Post by joehall on 2009-06-27
There is a button on the top of the laptop that under windows enables and disables the wireless card. This button has a blue LED. When the card is enabled the light is on...when no enabled the light is off....the light is off now and i can't turn it back on. could this be the issue?

---

### Post by Ayuthia on 2009-06-27
Sorry, I have not found a solution to this problem yet.  If I find one, I'll let you know.

---

### Post by kmb101 on 2009-06-27
There may not be a solution without getting an internet connection. I have the same card you do and I had the same problem but I have an ethernet port. My solution was to uninstall network-manager in synaptic and install a program called WICD (another network-manager. Ok course you would need to download the b43 driver for this to work. Good Luck!!!!

---

### Post by joehall on 2009-07-02
@kmb101 I think I might try your solution. I went to Ubuntu's Universe repository and grabbed WICD. Have placed the WICD's download on a USB stick and moved it to the desktop of my unbuntu laptop. Do I need to uninstall network-manager in synaptic? and then install WICD? If so could you give me the appropriate commands to use on in the terminal? The download file is on the desktop and is called wicd_1.5.9-2_all.deb

As i mentioned before i am some what of a linux n00b, but i am not affraid to use the terminal or learn how to hack a solution.

Thank you in advance for your help!

---

