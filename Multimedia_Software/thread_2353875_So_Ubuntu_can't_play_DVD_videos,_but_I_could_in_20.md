---
title: "So Ubuntu can't play DVD videos, but I could in 2005 on Red Hat"
date: 2017-02-25
forum: Multimedia Software
---

### Post by MechaMechanism on 2017-02-25
In 2005 (or somewhere around that time) I could play my DVD videos on Red Hat using my own custom compiled Xine-UI with buttery smooth frame rate, but I can't do that on Ubuntu in 2017.  I mean, I get the legal stuff, but after installing libdvdcss shouldn't it work just out of the box by now?

Can't stand Xine-UI and Mplayer is annoying and Mplayer and SMplayer won't even play.  So I tried VLC, but the DVD menu selections are all wonky.  I can't select the DVD menu that I want in VLC.  Tried Gnome video player, I see no obvious way to play disc.  Tried VLC latest Git, just a black screen with skipping audio.

Followed this how to; [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I just want a DVD Video player that has proper menu support and outputs stereo audio and can display English subtitles and works with Region 1.

My manufactured in 1998 DVD set top video player can play the Disc just fine and I'm playing the same videos now that I played in 2005.  The disc work in the set top player just fine.

Using System76 Wild Dog Pro.

Any thoughts on the Fluendo paid DVD app?  I just want an app to play DVD videos.

---

### Post by cariboo on 2017-02-26
Give Parole Media Player a try

[[img]https://s17.postimg.org/a8go5ek1n/Screenshot_2017_02_25_21_29_36.png[/img]](https://postimg.org/image/a8go5ek1n/)

---

### Post by MechaMechanism on 2017-02-26
> **cariboo said:**
> Give Parole Media Player a try

[[img]https://s17.postimg.org/a8go5ek1n/Screenshot_2017_02_25_21_29_36.png[/img]](https://postimg.org/image/a8go5ek1n/)

I tried it.  Got Gstreamer error.  But I figured out how to turn off DVD menu in Smplayer and now SMplayer works.

Parole seems promising.  I'd like to find a way to make it work as DVD menus are nice to have.  With parole the video is distorted and the sound is choppy and full of artifacts.

---

### Post by CharlesA on 2017-02-26
Does VLC support playing DVDs on Ubuntu?

I know you said it was choppy, but that sounds more like a hardware thing than VLC.

The VLC wiki mentions a few solutions for that.. no clue if they actually work or not tho:
[https://wiki.videolan.org/VSG:Video:Choppy/](https://wiki.videolan.org/VSG:Video:Choppy/)

---

### Post by mc4man on 2017-02-26
Your issues seem video output related though you didn't provide any info inc. which Ubuntu release & what is the Gpu on whatever your hardware is???
In both 14.04 & 16.04 tortem & vlc should handle dvd & dvd menus just fine (- though in 14.04 totem benefits  from a not default supplied grilo plugin, i.e. optical media plugin
inxi -b would suffice for some info

---

### Post by MechaMechanism on 2017-02-26
> **mc4man said:**
> Your issues seem video output related though you didn't provide any info inc. which Ubuntu release & what is the Gpu on whatever your hardware is???
In both 14.04 & 16.04 tortem & vlc should handle dvd & dvd menus just fine (- though in 14.04 totem benefits  from a not default supplied grilo plugin, i.e. optical media plugin
inxi -b would suffice for some info

Ubuntu 16.10; System76 Computer desktop with Intel® HD Graphics 530 (Skylake GT2) and Intel® Core&#8482; i5-6500 CPU @ 3.20GHz × 4 and 15.5 GiB memory.  64 bit.

I'm using VLC 3.0 from Git as a snap and the snap version of VLC gives permission error; can not read from drive.  I have included 2 screen shots.  The first screen shot is regular VLC 2.2.4 and the menus are rotated for some reason and when you click on a menu it takes you to the wrong menu.  Usually when selecting a menu in VLC you have to select the next menu down to get the one you want.  Totem video player has the menus right side up, but it has the same problem as VLC in trying to select the menus.

I bought the computer in December of 2015 and have never played any videos on it except the occasional video download.  Usually YouTube or Facebook.  First time playing any kind of video disc.

What other information do you guys need.  Any logs or terminal debug commands you need.

---

### Post by mc4man on 2017-02-27
For VLC snap, 
```
sudo snap remove vlc
```
```
sudo snap install --classic vlc
```
This will remove the default confinement that snaps have & allow access outside of $HOME

Also make sure vlc is using OpenGl as video output, (- hardware accelerated decoding is irrelevant as snaps don't support..

---

### Post by MechaMechanism on 2017-02-27
> **mc4man said:**
> For VLC snap, 
```
sudo snap remove vlc
```
```
sudo snap install --classic vlc
```
This will remove the default confinement that snaps have & allow access outside of $HOME

Also make sure vlc is using OpenGl as video output, (- hardware accelerated decoding is irrelevant as snaps don't support..

Did that, but still no go.  So I looked in .config/vlc and saw that the config files were for 2.2.2.  The non snap version of VLC is 2.2.4.  So on a hunch I deleted the VLC dir in .config.  Started the non snap version of VLC and got the first time run dialog box.  Then closed it and inserted the DVD disc into the drive and when asked to; selected the non snap version of vlc and what do you know; it worked!  VLC now works great.  The DVD menus are right side up and the mouse works like its supposed to in the menus.  I somehow also got Totem to work, but I have no idea how that happened.

Mplayer does not have menu support as far as I know, but it does work and MPV seems the same as Mplayer.  Smplayer has no menu support as well.  Parole player does not even work; something about Gstreamer error.

So I guess I'm satisfied with the non snap version of VLC.  Thank you fellows.

---

### Post by mc4man on 2017-02-27
> **MechaMechanism said:**
> Did that, but still no go.  
Just checked - even with confinement disabled a snap vlc can't use the system installed libdvdcss2 so it's worthless for dvd playback (encrypted disc's
Actually all snap media players are generally worthless atm...

For future info - snap installed apps would use a separate .config folder, i.e. ~/snap/the appname/a number folder/.config

---

### Post by MechaMechanism on 2017-02-28
> **mc4man said:**
> Just checked - even with confinement disabled a snap vlc can't use the system installed libdvdcss2 so it's worthless for dvd playback (encrypted disc's
Actually all snap media players are generally worthless atm...

For future info - snap installed apps would use a separate .config folder, i.e. ~/snap/the appname/a number folder/.config

That's too bad as a git version snap of VLC would allow us to check out the latest code.

---

