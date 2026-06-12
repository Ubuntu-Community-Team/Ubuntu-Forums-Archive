---
title: "cannot find input plugin for MRL - kaffeine DVD"
date: 2009-11-15
forum: Multimedia Software
---

### Post by bowens44 on 2009-11-15
I am getting an error 'cannot find input plugin for MRL ' when attempting to play a dvd in Kaffeine. all of the other movie players (mplayer,vlc,xine) work as they should.

I have googled but haven't found a solution.

Using Karmic Ubuntu 64 bit 

thanks

---

### Post by OzzyFrank on 2009-12-09
I actually just did a blog post on that:

[http://ubuntugenius.wordpress.com/2009/12/09/fix-cannot-find-input-plugin-for-mrl-dvd-error-in-kaffeine-mplayer-other-media-players-in-ubuntu/](http://ubuntugenius.wordpress.com/2009/12/09/fix-cannot-find-input-plugin-for-mrl-dvd-error-in-kaffeine-mplayer-other-media-players-in-ubuntu/)

Hope it's the fix you need, but I am pretty sure it would be. Cheers

---

### Post by SlappyPappy on 2010-01-02
Tried that but still can't get Kaffeine to work.

---

### Post by mc4man on 2010-01-02
not a big fan of kaffeine for dvd playback and a quick look suggests it will only play from /dev/dvd

**If** this is your problem, then better to change the dev links of your drive than use a symlink

This should prove informative in that regard, post results

```
sudo lshw -C disk
```
and ( run this in a maximized terminal so lines stay separate, 
 ```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by OzzyFrank on 2010-01-16
Hey **mc4man**: I am assuming you would need to edit that config file, so what would you need to add/change to get it to recognise **/dev/dvd** as being the disc drive from then onwards? Mine has lines like the following (which mentions "dvd", though have no idea if that means **/dev/dvd**, since no paths are mentioned anywhere):

**ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"**

Cheers

---

### Post by mc4man on 2010-01-17
@OzzyFrank
you're probably fine...
what can happen sometimes is a drive that is scsi-0:0:0:0 (/dev/sr0, /dev/scd0) can get a dev link of /dev/dvd1,and or /dev/cdrom1 or possibly higher

There are several possible reasons, most can simply be 'resolved' by editing the file back to basically nothing and re booting ( file will be re-written on boot

There are some hardware configs where with 2 dvd/cd drives you may wish to switch the links and very rarely where with one drive it gets /dev/dvd1 even with a re-write.

( when you replace a drive the file should be emptied and re-written, especially if one used sandisk flash drives w/U3 which get and occupy a /dev/cdromX link(s)

To reset simply go (in a maxed terminal
```
gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

and delete everything below this line, save and reboot
> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.


Note - issues from 70-persistent-cd.rules was much more likely back in gutsy thru intrepid, though still possible

---

### Post by Whiplash22 on 2011-07-18
> **bowens44 said:**
> I am getting an error 'cannot find input plugin for MRL ' when attempting to play a dvd in Kaffeine. all of the other movie players (mplayer,vlc,xine) work as they should.

I have googled but haven't found a solution.

Using Karmic Ubuntu 64 bit 

thanks

All of the replies I have read here border on ridiculous when the solution is actually MUCH simpler in my experience.  All you need is to install libxine1-codecs.  I use openSUSE, not Ubuntu, but I'm sure you can do it much the same.  I used SUSE's package manager, YaST and I'm sure you can search yours for it.  If you have to, install through terminal.  I'm sure it couldn't be too difficult although we SUSE users do have slightly different terminal commands i.e. zypper as opposed to apt-get, etc.  Just try your package manager first.  I guarantee you can skip all the other nonsense proposed here 99% of the time.

---

### Post by mc4man on 2011-07-18
I guess bowens44 can answer what was his issue if inclined, though if if read his post closely,(you do have to read occasionally in openSUSE I'd assume),  you'd notice he said he had xine installed and it  worked.
libxine1-ffmpeg is a dependency of xine (xine-ui) in ubuntu so one would assume it was installed.
Whether it was an improper /dev link or some other kaffeine style nonsense only the Op knows

---

