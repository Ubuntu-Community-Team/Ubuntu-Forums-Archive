---
title: "Why would I need to toggle between national and latin?"
date: 2011-01-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by philinux on 2011-01-23
This keyboard config during updates is still happening and very odd.

[EDIT]

Email 28/1/11
> Lots of people have reported keyboard layouts being broken in Natty in
one way or another.  This was due to a merge I did from Debian on
2011-01-05 which worked fine in my tests, but turned out to fail in a
number of common cases.  I've identified two major problems:

 * I added some misguided migration code which broke in the case of
   debconf preconfiguration (which most people use because apt does it,
   but I was testing with 'dpkg -i').  The effect of this was to reset
   the various keyboard settings to the first choice in their respective
   lists: if you have XKBMODEL="a4techKB21" and XKBLAYOUT="us,af" in
   /etc/default/keyboard, then this is what happened.  This also tended
   to result in keyboard questions being asked on every upgrade.

 * Versions of the installer-side keyboard handling code prior to Natty
   didn't always set the 'seen' flag for keyboard questions in the
   installed system's debconf database.  As a result, many people were
   asked the keyboard layout and variant questions again.

I've uploaded console-setup 1.57ubuntu5 to fix this.  When upgrading the
keyboard-configuration package to the new version, if it detects a
migration bug, it takes the old commented-out XKB* values from
/etc/default/console-setup and restores them, which should restore the
correct keyboard layouts for most people.  It will print messages on
standard error saying that it is doing so, but will not present any
debconf messages.

However, if you installed your system with an image from before
2011-01-05, upgraded it to current Natty, and then manually edited
/etc/default/keyboard or used 'dpkg-reconfigure keyboard-configuration',
the effect of this cleanup will be to *erase* those manual changes and
restore the configuration from before you upgraded console-setup.  I
hope that this will cause few problems, as the overwhelming likelihood
is that the previous configuration was more accurate.  I considered
presenting the debconf questions again, but given the significant
confusion already caused I felt that this would not improve the
situation.

Note that all of this only affects people who have upgraded through
Natty between Alpha 1 and Alpha 2.

If there's still a problem after all this, please let me know.  Sorry
for any inconvenience caused!

-- 
Colin Watson 

---

### Post by dino99 on 2011-01-23
im not sure but as i've understood that might be related to utf8 and other non utf8 fonts/languages

---

### Post by Quackers on 2011-01-23
It's certainly a pain, that's for sure!
Mine still shows USA in the applet but is actually typing as a GBr keyboard. I have to change it regularly, but sometimes on exiting the keyboard layout screen my desktop theme is changed! I have to reboot to fix it. It's all very odd.

---

### Post by philinux on 2011-01-24
Maybe it'll sort itself out by alpha 2.

---

### Post by cariboo on 2011-01-24
I just set it to none, just scroll down to the very bottom.

---

### Post by philinux on 2011-01-24
> **cariboo907 said:**
> I just set it to none, just scroll down to the very bottom.

Do you still get the GBR icon in the notification are? And USA layout pops back up in keyboard layouts, even if deleted.

---

### Post by cariboo on 2011-01-24
I don't get any notification at all, I had one system set to USA and Canada, I was getting the french keyboard, I did a fresh install, and set the toggle to none, and haven't seen the notification icon at all.

---

### Post by mc4man on 2011-01-24
I believe there were some changes to the  keyboard-configuration package that should make this not happen anymore though not sure if it will be the same for an updated install vs. a new install (from iso after 1/05 or so
(is not an issue here at all on 2 recent installs though I do use usa layout set during the install

There's a lot in the changelog concerning this and something about 'latin' that didn't pay much attention to.

---

### Post by efflandt on 2011-01-24
When that first came about (and every time it comes up in updates), I have always selected not to use anything to toggle the keyboard switcher.  Earlier I did end up with the keyboard switcher applet listing USA and Afghanistan.  But since I removed Afghanistan from the keyboard list, the applet has disappeared, and as far as I can tell, remains as USA keyboard only through subsequent updates.

---

### Post by Quackers on 2011-01-24
I've just run the new keyboard config update and my applet shows USA but my keyboard is still typing GBr.......for the moment  :wink:  :-)

---

### Post by jocko on 2011-01-25
I don't see any point of having a key to toggle keyboard layout. My keyboard is Swedish, all keys are labelled according to the Swedish layout. Toggling to another layout does not magically replace the physical keys on my keyboard.
And the silly message says "toggle between national and latin" but that's not even true. I tried it, and it toggles between US and Swedish which both use latin characters (swedish have three more letters and many of the characters like -, _ , ^, @, #, £, \, | and so on are on different keys in the different layouts).

[B]Anyway, this seems to be a permanent fix to keep the correct keyboard layout:
[/B]
Log out. On the login screen, click your username, but before you log in pick the correct language and keyboard layout in the drop-down menus that appear on the bottom panel.

---

