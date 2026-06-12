---
title: "Installed ATi driver now i can't boot up"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by Mark Whiten on 2006-08-18
Hi all,

I just installed the ATi drivers following this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) and afterwards Ubuntu doesn't boot up. I see the splash screen with everything loading and then the screen goes black and hangs.

It's 64bit dapper if that helps. Any suggestions welcome :)

---

### Post by Ziox on 2006-08-18
> **Mark Whiten said:**
> Hi all,

I just installed the ATi drivers following this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) and afterwards Ubuntu doesn't boot up. I see the splash screen with everything loading and then the screen goes black and hangs.

It's 64bit dapper if that helps. Any suggestions welcome :)

When it boots up, are you sure it hangs?  Do you hear the drum sounds for Ubuntu login Screen?  If you can hear anything, then it means that it's just X that's not starting right.

to make your computer useable again, boot up, then at the grub menu, hit esc, and enter recovery mode (which will bring you to the command line)

now enter sudo dpkg-reconfigure xserver-xorg

make sure you choose the right driver for your card.  Since fglrx doesn't seem to work w/ your card, choose either ATI or Radeon. But feel free experiment with fglrx.

After that step, enter sudo reboot to reboot the computer, and if done correctly, the computer should boot and log in fine.

Hope this helps.

---

### Post by Greycloak on 2006-08-18
I can tell you from experience that the xorg-driver-fglrx from the repo works fine for ATI cards. The fglrx 8.27.10 from ATI is definitely flaky though.

---

### Post by Mark Whiten on 2006-08-18
There aren't any sounds at all and there is no hd access. Shall i still follow the steps you listed?

Thanks for the replies :)

---

### Post by Mark Whiten on 2006-08-18
Well i tried the steps in your post, Ziox, and selected the ATI driver. I rebooted and got an error saying that it couldn't load the GUI. I looked at the error message and it had a list of graphics cards (all ati) but it only had up to the Radeon X850XTPE whereas my card is a Radeon X1800XT. So it seems that the drivers haven't been updated to support my newer graphics card?

Is there an easy way for me to remove the drivers through the command line or will i have to boot to a live distro and delete the specific files?

Thanks once again for your help :)

---

### Post by Ziox on 2006-08-18
> **Mark Whiten said:**
> Well i tried the steps in your post, Ziox, and selected the ATI driver. I rebooted and got an error saying that it couldn't load the GUI. I looked at the error message and it had a list of graphics cards (all ati) but it only had up to the Radeon X850XTPE whereas my card is a Radeon X1800XT. So it seems that the drivers haven't been updated to support my newer graphics card?

Is there an easy way for me to remove the drivers through the command line or will i have to boot to a live distro and delete the specific files?

Thanks once again for your help :)

if you used the first method on the website you provided, then I think

sudo apt-get remove xorg-driver-fglrx would do

however, removing the ATI driver, I would imagine to be a little tougher...

---

### Post by Mark Whiten on 2006-08-18
I seemed to have solved it without removing the drivers.

I just received my Kubuntu discs through the post so i booted into that to give it a try. While playing around i noticed that my videocard driver was 'vesa'. I rebooted into Ubuntu and reconfigured xserver using the vesa driver. Now it all works fine! Thanks for your help though, it's been very useful :)

---

