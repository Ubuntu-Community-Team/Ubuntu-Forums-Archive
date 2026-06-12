---
title: "Cannot play audio CDs"
date: 2008-06-02
forum: Multimedia Software
---

### Post by HyperHacker on 2008-06-02
I can't play any audio CDs in Ubuntu. When I insert one, Totem opens and says "An error occurred; Location not found."
MPlayer reports the same:
```
Playing cdda://.
Can't open CDDA device.
Failed to open cdda://.
```Amarok just says "cannot read AudioCD" in the status bar.

The discs play in standalone players, and data CDs read OK.

---

### Post by Ashrael on 2008-06-02
hmm, i looked at my amarok settings and i think it is supposed to say /dev/cdrom in SETTINGS>CONFIGURE AMAROK/ENGINE.

---

### Post by aeiah on 2008-06-02
what happens if you try playing it from root?

```
sudo totem
```

---

### Post by HyperHacker on 2008-06-03
"Play Audio Disc" is grayed out. "Play CD-ROM 1" shows the message "Totem was not able to play this disc. Please check that a disc is present in the drive." Those options only even appear the first time I open the menu.
> **Ashrael said:**
> hmm, i looked at my amarok settings and i think it is supposed to say /dev/cdrom in SETTINGS>CONFIGURE AMAROK/ENGINE.That's what mine says.

Is it possible for the drive to be defective, such that data CDs work but audio CDs don't? I don't think I've ever actually used an audio CD in this drive before, as it's fairly new. I've tried a few other discs though, that I know have no form of copy protection and can be read by any CD-ROM drive.

It looks like the disc I tried first has a ring around the inside of the data track, that could be another session containing some sort of copy protection software or something... I would hope Ubuntu is smart enough not to automatically run a program it finds on an audio CD though. :P (Physical protection wouldn't explain why other discs don't work, unless it's damaged the drive somehow.) Could it be that something got confused seeing a data+audio disc? It doesn't show up in GParted, so I don't know how to go about examining it, except to try it in another computer, but I don't have time for that right now as I'm leaving for work in about 5 seconds.

---

### Post by mc4man on 2008-06-03
@ HyperHacker
If you're running xubuntu you're in luck, it's set up to deal with multimedia just like in gutsy, ie. you can do what you want.(particularly with 2 drives)
run this anyway to ck. on your drives
```
sudo lshw -C disk
```
As far as playing cds, dvds the setup is the same as gutsy - removable drives and media
for cd's if you want amarok go applications -> settings -> settings manager ->  removable drives and media -> multimedia. For cds ck. play when inserted and use this command ```
amarok -cdplay %d
``` Insert your cd and amarok will pop up, load cd and start playing. (_the default device will be automatically set_). if you have 2 drives when you insert cd in 2nd drive it will play and the _default device will be dynamically switched for you_ and will stay on that drive till you insert cd into 1st. drive, ect. In other words you'll never have to set it
For dvds using vlc use ```
vlc %m
``` in dvd box.
totem is looking at wrong or nonexistent device, 1st command posted will help square that away. Or install totem-xine (leave totem gstreamer installed) and run 
```
sudo update-alternatives --config totem
``` choose 2 and make config changes in home -> username -> .config -> totem -> xine_config

---

### Post by HyperHacker on 2008-06-04
Thanks, it looks like mine is /dev/cdrom1 for some reason. I pointed Amarok at that and it works, though takes ages to load the playlist. O_o Is it safe then to just link /dev/cdrom to /dev/cdrom1? I only have one CD drive, there's never been 2 installed, I just had to replace one.

I'm not especially concerned about Totem as I only use it as a "spare" video player for when MPlayer won't play something.

---

### Post by mc4man on 2008-06-04
take a read thru here
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)
and if it looks similar post results of sudo lshw -C disk
and the contents of the 70-persistent-cd.rules file

it does take it a bit to load the cd

edit ; even if you don't have 2 listings you may want to edit the ....rules back to links of dvd, cdrom cdrw ect. - less hassle in the end due to apps defaulting to those vs. the 1 links

just saw this > I just had to replace one I believe when you replace a drive the links given to it in ....rules are 'reserved' in case the drive is returned and the new drive is assigned ones that are 1 up. i'd just edit the new drives links in ...rules removing the 1 and reboot

---

