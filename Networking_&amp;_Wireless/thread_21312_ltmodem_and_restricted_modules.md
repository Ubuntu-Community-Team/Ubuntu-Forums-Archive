---
title: "ltmodem and restricted modules"
date: 2005-03-21
forum: Networking &amp; Wireless
---

### Post by hogweed on 2005-03-21
Hi!

I have installed the Kubuntu preview on a Dell Latitude L400(?) with a Lucent modem. I have had this work with kernel 2.6.10 under MEPIS by adding pci=routeirq to the boot commands. However, with Ubuntu and Kubuntu Hoary, I am having no luck.

The ltmodem module should be in the restricted-modules, which gets installed by default. When I try to insmod lt_serial, I get an error. Then, upon the next boot, networking fails and X fails. ](*,) 

This has got to be a pretty simple thing, but I am having no luck. The previous posts on the ltmodem deal with Warty, and I would like to be able to use Hoary (and not MEPIS).

Any suggestions at all are welcome, and I can't believe that I am the only one having this problem!

hogweed

---

### Post by m4ng0 on 2005-03-21
Download the latest driver from:
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)
(the file should be [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7.tar.bz2)](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7.tar.bz2)).

From Synaptic install:
    *  linux-headers
    *  build-essential

Then compile the drivers. They worked ok with my Lucent modem (on a desktop pc though...).
If you use these drivers, you have to type:
sudo modprobe -v ltserial
to load the module (not lt_serial).

---

### Post by hogweed on 2005-03-22
[QUOTE=m4ng0]Download the latest driver from:
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)
(the file should be [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7.tar.bz2)](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7.tar.bz2)).

From Synaptic install:
    *  linux-headers
    *  build-essential

Then compile the drivers. They worked ok with my Lucent modem (on a desktop pc though...).
If you use these drivers, you have to type:
sudo modprobe -v ltserial
to load the module (not lt_serial).[/QUOTE]

I will try this if all else fails, and thanks for the tip (I hadn't seen that site for the drivers before). I really would like to make this work with the ubuntu restricted-modules, though in good part so that I don't have to fetch and recompile them with each kernel change. Theoretically the restricted-modules should work, and I think that I am close to solving this. I will write a post once that is done.

Thanks again!

---

### Post by hogweed on 2005-03-23
SOLVED!

Just briefly, for anyone interested, this is what I did to get the Lucent winmodem up and running without recompiling drivers. I have condensed what I did here, drawing on different posts to these forums, the linmodems.org forums and the debian lists. Thanks to everyone!

1. make sure that you have the restricted-modules installed. This was done by default in the install of Kubuntu Hoary preview.

2. put lt_serial and lt_modem in /etc/modules in order to get the modules loaded on boot. The modem device will appear as /dev/ttLTM0 (that is a zero at the end).

3. since udev rewrites /dev on each boot, and since kppp doesn't like to use /dev/ttLTM0, you need to have a symlink created on boot (from /dev/ttLTM0 to /dev/modem is easiest, I think). To do this, create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:  
 #ltmodem
 KERNEL="ttLTM0", SYMLINK="modem"

4. since the 2.6.10 kernels have some problems with these modules, put the following in the grub boot commands (at the place where it will get updated!):
pci=routeirq

5. run grub-update to update grub

6. If you are going to use kppp, edit the file /etc/ppp/options and comment out the line that says "auth" (ie., make it "#auth").

7. reboot and configure your dial-up service, and it should be good to go!

Wonderful, wonderful Ubuntu and other Linux forums -- yet another reason to avoid closed source operating systems!

-- hogweed

---

### Post by dbutcher on 2005-03-23
Thanks for this very helpful post.
Just one question:  Why is it /dev/ttLTM0 and not /dev/ttyLTM0 ?

---

### Post by hogweed on 2005-03-24
[QUOTE=dbutcher]Thanks for this very helpful post.
Just one question:  Why is it /dev/ttLTM0 and not /dev/ttyLTM0 ?[/QUOTE]

I am really not sure, but that is the way it worked out on my system (and I imagine all others). I know that previously this created /dev/ttyLT or something like that, and that the modules vary from ltmodem to lt_modem, etc. 

A bit of a moving target, it seems, but the above description was successful using nothing but the Hoary repositories, so it should be good for *at least* this release.

-- hogweed

---

### Post by jasplund on 2005-04-07
How do I do this? "4. since the 2.6.10 kernels have some problems with these modules, put the following in the grub boot commands (at the place where it will get updated!):
pci=routeirq"

---

### Post by hogweed on 2005-04-08
[QUOTE=jasplund]How do I do this? "4. since the 2.6.10 kernels have some problems with these modules, put the following in the grub boot commands (at the place where it will get updated!):
pci=routeirq"[/QUOTE]

I saw your post in the other thread, and I do think that you should follow the recommendation of the person who said to hit "esc" at boot and manually add it in once just to check it out.

If it works, do this:

sudo nano /boot/grub/menu.lst

scroll down and look for the section that looks like this:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda5 ro


Add the comment at the end of the line that starts "#kopt=root"

In this case it would read

#kopt=root=/dev/sda5 ro pci=routeirq

Save and exit.

Issue this command:

sudo update-grub

This will add the command in at the end of the lines of the actual kernel entries. When you reboot it will be effective.

The advantage of putting the boot command at that particular point is that it will, as it suggests, "automagically" update the boot comands even when your kernel is updated, etc. Pay attention though: at some point this won't be needed anymore because the kernel will get patched/fixed. So if you end up with strange behavior later, you might need to remove it.

I hope this helps.

-- hogweed

---

### Post by robertobech on 2005-04-14
I've followed your instrctions, and kppp dials, but can't connect. I start hearing all those noises, but then they all stop and that's it. I know my lucent modem does work, because I used to try it with a brazilian distro called Kurumin that installed it properly through a script.

Did you change anything on your connection string or something like that? Please help me here, I feel that I'm really close to make my lucent work.

---

### Post by dsavel on 2005-04-15
[QUOTE=robertobech] I start hearing all those noises, but then they all stop and that's it. [/QUOTE]

I had exactly the same problem with default drivers lt_serial and lt_modem in package linux-restricted-modules for 686 tough I followed instructions in this thread. I spent some time to find what's the matter, but I'm not a programmer, I couldn't understand what's wrong. I also noticed that minicom couldnt connect to modem with default drivers. Though the standard tool for network settings made the modem to dial number and have a connection, it couldn't autorize properly to PAP service. 

Then I decided to compile the modules package from linmodems site, as also described here, and it worked! Finally I write this in Ubuntu! 

Something different from SUSE that I used before - I cannot see connect speed in log and no standard tool for it. Though SUSE was a huge 'ideologically-wrong' monster, it detected and installed ltmodem drivers without pain.

---

### Post by robertobech on 2005-04-16
[QUOTE=dsavel]I had exactly the same problem with default drivers lt_serial and lt_modem in package linux-restricted-modules for 686 tough I followed instructions in this thread. I spent some time to find what's the matter, but I'm not a programmer, I couldn't understand what's wrong. I also noticed that minicom couldnt connect to modem with default drivers. Though the standard tool for network settings made the modem to dial number and have a connection, it couldn't autorize properly to PAP service. 

Then I decided to compile the modules package from linmodems site, as also described here, and it worked! Finally I write this in Ubuntu! 

Something different from SUSE that I used before - I cannot see connect speed in log and no standard tool for it. Though SUSE was a huge 'ideologically-wrong' monster, it detected and installed ltmodem drivers without pain.[/QUOTE]
 Yes! I compiled it and it worked here too!

In fact, after compiling it still wasn't working... I was trying to connect through kppp. Then I started kppp as root (with sudo) and it worked! Thanks for your opinions...

---

### Post by hogweed on 2005-04-16
[QUOTE=robertobech]Yes! I compiled it and it worked here too!

In fact, after compiling it still wasn't working... I was trying to connect through kppp. Then I started kppp as root (with sudo) and it worked! Thanks for your opinions...[/QUOTE]
 robertobech:

Odd. The only thing that I can think of is a missing "pci=routeirq" in the boot commands. Did you put that into grub and then do update-grub?

Also, you shouldn't have to run kppp as root. I don't know what to tell you -- the restricted-modules worked fine for me here using the steps I mentioned above.

Glad its working for you, though.

-- hogweed

---

### Post by brunog on 2005-07-10
Hi guys,
I am new to the Linux environment and trying to catch up as fast as possible.  I am not a programmer and therefore do not understan all things mentioned.
I run a Pentium 4 , 2.6 GHz with 512 MB

I have been trying to get my "Lucent Microelectronics 56k WinModem" up and running in Ubuntu Version 5.04 for the past 2 weeks.
I have read so many threads and advise that my heads is starting to hurt!!

I have followed the advice provided in: WinModemLucent Wiki. : "How to get an Internal Lucent/Agere Modem to Work on Hoary" and this is the closest I got to a working connection.
I use either pon/poff or the Modem dialer in Ubuntu.  The modem dials, and strats wizzing away.  Then silence and eventually it disconnects.
I have seen the comments in this Thread regarding loading latest driver from:
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/).
In this thread it refrers to :ltmodem-2.6-alk-7.tar.bz2.
Based on another thread I have previously downloaded :ltmodem-8.31a10.tar.gz.
I am not sure which one is the latest one, or what the efect will be if I now compile ltmodem-2.6-alk-7.tar.bz2 "over" ltmodem-8.31a10.tar.gz.

I have also noticed some people say that wvdial works when pon does not.  Have tried this, but do not know how wvdial works.  I have read the text files for wvdial,  but they refer to the modem as being something other than dev/ttLTM0.

At this point I am a bit frustrated and would like very much to get on the web with Ubuntu.

Any help will be much appreciated!!

Please let me know if I need to provide more info.
Thank you

---

### Post by Ragnar on 2005-07-21
[QUOTE=hogweed]I saw your post in the other thread, and I do think that you should follow the recommendation of the person who said to hit "esc" at boot and manually add it in once just to check it out.

If it works, do this:

sudo nano /boot/grub/menu.lst

scroll down and look for the section that looks like this:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda5 ro


Add the comment at the end of the line that starts "#kopt=root"

In this case it would read

#kopt=root=/dev/sda5 ro pci=routeirq

Save and exit.

Issue this command:

sudo update-grub

This will add the command in at the end of the lines of the actual kernel entries. When you reboot it will be effective.

The advantage of putting the boot command at that particular point is that it will, as it suggests, "automagically" update the boot comands even when your kernel is updated, etc. Pay attention though: at some point this won't be needed anymore because the kernel will get patched/fixed. So if you end up with strange behavior later, you might need to remove it.

I hope this helps.

-- hogweed[/QUOTE]
 Hogweed thank you for your posts.  I have made the changes that you recommend but have had only partial success.  The network setup procedure atill cannot autodetect the modem and manually selecting dev/modem doesn't work.  If I type in dev/ttLTM0 and then press the Activate button, the modem dials but doesn't connect.  It continues to dial at intervals until I deactivate.  

I may have misnamed the 10-local.rules file.  Are the first 3 characters one zero hyphen?  Hard to tell with this font.

How do I tell whether I am using kppp or something else.  Is there a link that explains this?  I haven't done anything about this as I think I am on ppp.

Some later posts suggest that the pre- installed 686 modules don't work.  I am currently using the 386 kernal even though I am on an Nforce2 integrated-everything Leadtec motherboard with an Athkon 200+.

My modem is a Dynalink with mars chipset and works fine under Win98SE.  I bought it several years ago because even then there were supposed to be Linux drivers for it.

Please help!  This is driving me crazy.  If I can't even get the drivers preloaded by Ubuntu to work how am I ever going to get my Compaq 2145 laptop with a Connexant chipset to work?  So far the "Linux for human beings" tag that stares me in the face each time I do battle with these problems seems like a joke in increasingly poor taste.

---

