---
title: "I want my boot text back"
date: 2011-01-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Aide9aic on 2011-01-03
Dunno why, but graphical boot screens bug me. I don't need to look at a pretty picture; instead I love to watch those boot messages scroll by. Always before I could get this by removing the "splash quiet" items from the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub and commenting out the GRUB_HIDDEN lines.

Now this no longer works: while I still see the kernel selection menu, the background is purple. No messages scroll by, but there appears a few lines of something like black text on a black background.

I removed the execute flag from 05_debian_theme in /etc/grub.d and that got rid of the purple background: now it's just plain black during the boot.

Do I need to configure some Plymouth thing that's new in Natty? Or what?

---

### Post by dino99 on 2011-01-03
you need to update-grub

---

### Post by Aide9aic on 2011-01-03
Yes, I did that.

---

### Post by zika on 2011-01-03
Try adding GRUB_GFXPAYLOAD_LINUX=text to /etc/default/grub ...
(update-grub, after that...)

---

### Post by praveenmarkandu on 2011-01-03
if you just remove plymouth would it not fall back to text mode?
*edit: or maybe just uninstall plymouth-theme-ubuntu-logo*

---

### Post by Harry33 on 2011-01-03
> **praveenmarkandu said:**
> if you just remove plymouth would it not fall back to text mode?
*edit: or maybe just uninstall plymouth-theme-ubuntu-logo*

Yes that is a better option.
In fact, packages plymouth and libplymouth2 cannot actually be uninstalled, because mountall depends on them both.

---

### Post by Aide9aic on 2011-01-03
Grr, this seems a whole lot more difficult that it ought to be. I removed everything related to Plymouth except the two items that would break dependencies: plymouth and libplymouth2. There were some complaints about missing links in /lib/plymouth/themes (sorry I forgot the exact details) but then when update-initramfs executed, there were no errors.

I also added GRUB_GFXPAYLOAD_LINUX=text to /etc/default/grub. Curiously, eventhough the GRUB_GFXMODE line remains commented out, GRUB puts my graphics card into a high resolution. After making these changes, I still don't see most of the boot messages...the only lines that appear are the ones indicating the begin and end scripts. I uncommented the GRUB_TERMINAL=console line; this time GRUB runs in text mode but I'm still not seeing the boot messages (other than the same ones as before).

---

### Post by zika on 2011-01-03
Long shot:
-check the file /etc/initramfs-tools/conf.d/splash
-check if plymouth lurkes in update-rc.d (even though You erased splash)...
I do have all the text present, and I like to have it, too...

---

### Post by Aide9aic on 2011-01-03
Thanks for the suggestions...but no dice on either one: /etc/initramfs-tools/conf.d/splash doesn't exist and there's no mention of "plymouth" in update-rc.d.

A couple files in /etc/init looked promising... in plymouth.conf I commented out the "exec /bin/plymouth show-splash" line and in plymouth-splash.conf I commented every line. Ran update-initramfs. Rebooted and still a mostly blank screen after kernel selection, except for the same few lines about processing scripts.

I feel like I'm trying to hack something that ought to be quite simple!

---

### Post by hugmenot on 2011-01-03
My problem with plymouth is that with a slimmed boot order and an SSD boot drive plymouth only splashes for a fraction for a second making it unsightly. Just a black console would be good.

---

### Post by oldfred on 2011-01-03
Just like in old grub legacy, edit out the quiet & splash. Just with grub2, you now do it in /etc/default/grub and then run a sudo update-grub.

GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=Red]quiet splash[/COLOR]"

---

### Post by Starks on 2011-01-03
Isn't Recovery Mode text-boot enough?

---

### Post by Harry33 on 2011-01-04
> **hugmenot said:**
> My problem with plymouth is that with a slimmed boot order and an SSD boot drive plymouth only splashes for a fraction for a second making it unsightly. Just a black console would be good.

As long as Plymouth has been in Ubuntu, there has been a lot of unresolved problems with it. This is surely not only a Natty thing.
First there were issues with proprietary drivers and Nvidia, now with older graphics cards, plus that Plymouth is now also ugly with the antialiasing bug, and on and on.

Now that Natty grub2 has a default color (easy to edit too) background, do we need the Plymouth at all?
Is it so important to see a logo to know that we are really using Ubuntu on each boot and reboot?

---

### Post by Yougo on 2011-01-04
it reminds me of the days when people across the internet were screaming at canonical to switch to plymouth. now that they have, we're not really better off it seams. especially considering what they do with it (plain purple background, logo and a throbber, not even a process bar)

nothing xsplash, or even usplash couldn't do.
i suppose there are technical reasons for using plymouth...

as to your wish, maybe you could check what switches the recovery mode uses to boot and copy that?

---

### Post by Starks on 2011-01-04
Flicker-free, KMS-friendly boot-up is more important than a pretty boot-up.

---

### Post by Yellow Pasque on 2011-01-04
OK, I get it, folks. You want me to update my plymouth liberation PPA (mediahacks) for natty. Processing...

EDIT: Done. Get mountall and/or cryptsetup from here and then you can remove plymouth without taking out half of the actually useful packages: [https://launchpad.net/~dtl131/+archive/mediahacks](https://launchpad.net/~dtl131/+archive/mediahacks)

---

### Post by Harry33 on 2011-01-05
> **Temüjin said:**
> OK, I get it, folks. You want me to update my plymouth liberation PPA (mediahacks) for natty. Processing...

EDIT: Done. Get mountall and/or cryptsetup from here and then you can remove plymouth without taking out half of the actually useful packages: [https://launchpad.net/~dtl131/+archive/mediahacks](https://launchpad.net/~dtl131/+archive/mediahacks)

That is a good idea.
Actually Ubuntu's mountall should only recommend plymouth, not depend on it.
This is surely a bigger issue concerning concepts like "dependency hell" and "freedom of choice".
"Depends" should IMO used only when a package really needs the target.
"Recommended" should be used if the target clearly enhances the package.
"Suggested" should be used if the target is only somehow useful to the package.

---

### Post by Yellow Pasque on 2011-01-05
There is actually a bug report about this, but I won't bother to link to it because it's one of those "won't fix" things. Ubuntu is not the best distro for "freedom of choice." The devs will be passive-aggressive <snip> at times (I say that with love), but you can usually work around it with PPA's

---

### Post by zika on 2011-01-05
If You are brave enough You could try:
```
mkdir ~/zika
sudo mv /etc/init/plymouth* ~/zika/.
sudo reboot now
```
[COLOR="Red"]It works at my place but I do not make any promises...
You're doing it on Your own risk...
I do not giveany guarantees...[/COLOR]

If You want to revert everything to original state, just```
sudo mv ~/zika/plymouth* /etc/init/.
```...

---

### Post by cgroza on 2011-01-05
Use startupmanager, it has an option for that.

---

### Post by zika on 2011-01-05
> **cgroza said:**
> Use startupmanager, it has an option for that.
It works with Natty and, especially, with new options in GRUB2...?

---

### Post by Sworddragon on 2011-01-06
I have the same problem too. At the booting the screen is a short time purple and the until nearly the end black. Only at the end I see lines that VirtualBox has problems and so.

My configuration:

GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_GFXPAYLOAD_LINUX=1680x1050-24


I have written exit 0 in the first line of all plymouth files in /etc/init and uncommented GRUB_TERMINAL=console but this hasn't changed anything. Only the single user mode shows me at booting all lines. I have this problem on 3 different computer with the same configuration.

---

### Post by Yellow Pasque on 2011-01-06
Look a few posts up and try the mountall from my PPA. Then you can remove plymouth (though that's a workaround and the bug should be fixed).

---

### Post by Starks on 2011-01-06
I don't know why people still recommend startupmanager.

It's been useless since Karmic.

---

