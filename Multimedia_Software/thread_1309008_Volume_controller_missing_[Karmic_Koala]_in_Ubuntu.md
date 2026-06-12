---
title: "Volume controller missing [Karmic Koala] in Ubuntu 9.10"
date: 2009-11-01
forum: Multimedia Software
---

### Post by mohan1311 on 2009-11-01
Post my upgrade to Ubuntu 9.10, i faced the same issue as in 9.04 in which my Mic did no work till i uninstalled pulse audio. In Jaunty, i haveno issue, in karmic after removal of pulse audio my sound & mic works but the volume control icon in panel is missing & under preferences -> sound i get the message 'Waiting for sound system to respond'.

i am also not able to increase decrease my volume using hotkey in my laptop

any suggestions?

-Mohan

---

### Post by eugen_nicoara on 2009-11-02
I'm also having this problem.

---

### Post by daugusto_go on 2009-11-02
I have the same problem.

---

### Post by Eman64 on 2009-11-02
Same here. But I also have 0 sound.

---

### Post by SlugSlug on 2009-11-02
same for me to

---

### Post by its_jon on 2009-11-02
same here :(

---

### Post by karlwilbur on 2009-11-02
no sound ++.

I am looking into a fix. I'll update with more detail as I obtain it.

---

### Post by its_jon on 2009-11-02
Check your 

/etc/pulse/default.pa file

Mine was corrupt... After restoring it I got all sound function back.

well sort of... Im still struggling to get my main envy24 soundcard to work in 9.10 but thats a different thread !

---

### Post by djgrant on 2009-11-03
Same here!

---

### Post by VertexPusher on 2009-11-03
In Karmic, Gnome's default volume control was replaced by one that works only with PulseAudio.

There are three alternatives to work around the problem:
[LIST]
[*]Install **gnome-alsamixer** as a replacement for the old volume control. It won't show up in the system tray but you can put a launcher next to the tray, so you can access it as quickly as the old volume control.
[*]Install **kubuntu-desktop** and change your login session to KDE. Kubuntu does not depend on PulseAudio in any way.
[*]If you want to keep Gnome and the original volume control, switch to Debian. There are no PulseAudio dependencies in Debian's version of Gnome. Debian has a policy of not adding beta level software to stable releases. They also try to keep things separate and modular instead of making unrelated things (such as desktop environments and sound daemons) depend on each other.[/LIST]

---

### Post by redLeopoldo on 2009-11-09
Had same issue on a Samsung NC10. In my case after updating to 9.10 from 9.04 the notification area was not part of the panel. After adding a Notification area to the panel it was populated by volume control and some other icons (bluetooth etc)
Hope this helps someone

---

### Post by anando on 2009-11-24
> **redLeopoldo said:**
> Had same issue on a Samsung NC10. In my case after updating to 9.10 from 9.04 the notification area was not part of the panel. After adding a Notification area to the panel it was populated by volume control and some other icons (bluetooth etc)
Hope this helps someone

For what it is worth, here are my observations:
* I too 'lost' my volume control icon in the notification panel when I removed pulseaudio
* and panicked and looked up the forums for help
* However, after re-installing pulseaudio, my volume control icon reappeared immediately.

Curious observation:
* Even if the existing users (at the time of upgrade Jaunty -> Karmic) don't see the volume controller, try creating a new user. New user *has* the volume controller by default. This leads me to believe that regular users need to delete some configuration file or directory after the upgrade for the volume controller to be seen. How come the community hasn't figured out a fix yet.

Last but not least: thank God I finally took the plunge for Mac OSX. Ubuntu has been steadily regressing and it's about time we got rid of this trash. Before, it used to be the case that every new Ubuntu release would fix problems in the previous version. Now, users are f**king wary that a new release would actually break something that used to work before. The only thing that Ubuntu devs are worried about nowadays is to make it look nice. Sad to see that they lost the plot after their initial heady days. I have been a linux user (luser) for the last 10 years (yes, I used to run it on my 15" MBP). But seriously, how long do you expect me to wait to get the bas**rd sound right. How long before i don't have to worry about and juggle with alsa, esd, pulseaudio, jack blah blah blah after every Linux installation before I can get the sound right. Another century? Yeah rt.

---

