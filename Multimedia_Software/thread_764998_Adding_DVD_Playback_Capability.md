---
title: "Adding DVD Playback Capability"
date: 2008-04-24
forum: Multimedia Software
---

### Post by Exsecrabilus on 2008-04-24
Go [here](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability) for the Gutsy guide on how to add DVD playback capability.

It worked on Gutsy, but it won't work on Hardy.

Before I had Internet connection on Gutsy, I did *sudo /usr/share/doc/libdvdread3/install-css.sh* and it gave me a link to where I was supposed to download **libdvdcss2**. Therefore I could then manually go to the side and download the .deb package.

Could someone tell me how to add DVD playback capability on **Hardy Heron AMD64**? Or at least tell me the site so I can manually install? Thanks.

---

### Post by odin79 on 2008-04-24
I also have problems with DVD playback after upgarding from Gutsy to Hardy. My DVD worked flawlessy in 7.10. I also tried to guides for Gutsy but no luck so far in Hardy. What do we need to do to play DVD-movies?

Thanks!

---

### Post by cor2y on 2008-04-24
First Enable the medibuntu repos [www.medibuntu.org]("http://www.medibuntu.org") to your source list (they show you how at the medibuntu site)
Update your source list ```
 sudo apt-get update
```Then remove this package ```
 sudo apt-get remove totem-gstreamer
```Next install these packages```
 sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libdvdnav libdvdread libdvdcss2
```The reason to remove totem-gstreamer is because while it can play dvds it cannot yet use dvd menus so depending on how the dvd is authored you might end up only being able to view the trailers section of the dvd instead of where the movie is and there also depending on how it was authored there might be no chapter stops. Totem-xine on the other hand has dvd menu navigation and the ability to use chapter stops etc.
If you prefer totem-gstreamer (you can find the plugins using add/remove via Application->Add/Remove) then just install all gstreamer plugins in addition to all the libdvd plugins libdvdnav libdvdread etc.
Then you can play dvds.

---

### Post by ubuntu-freak on 2008-04-24
> **Exsecrabilus said:**
> Go [here](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability) for the Gutsy guide on how to add DVD playback capability.

It worked on Gutsy, but it won't work on Hardy.

Before I had Internet connection on Gutsy, I did *sudo /usr/share/doc/libdvdread3/install-css.sh* and it gave me a link to where I was supposed to download **libdvdcss2**. Therefore I could then manually go to the side and download the .deb package.

Could someone tell me how to add DVD playback capability on **Hardy Heron AMD64**? Or at least tell me the site so I can manually install? Thanks.

 
Here is the direct link:
 
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)
 
I recommend you watch DVDs with VLC also.
 
To the other poster, have a look at part 4 of my how-to (second from the bottom in my sig). 
 
Nathan 
 
P.S. Don't remove totem-gstreamer, you can have both totem-gstreamer and totem-xine installed at the same time in Hardy. It was never a good idea to remove Gstreamer though.

---

### Post by odin79 on 2008-04-24
I followed your instructions cory, but no luck. I get the message "Couldn't find package libdvdread", and the same for libdvdnav. I have libdvdread3 and libdvdnav4 installed, are those correct?

As for the other libraries I already had them installed. Any other hints?

---

### Post by cor2y on 2008-04-24
yes thats them sorry for forgetting the new number addons.
And thats about it.
Totem-xine or gstreamer should now be able to handle dvd playback.
To make totem-xine the default dvd player (if you decide to keep totem-gstreamer) in nautilus (the file manager for ubuntu) go to Edit->Preferences the Media Tab and under dvd select Open Movie Player (Xine)

---

### Post by duckgoesoink on 2008-04-26
> **cor2y said:**
> To make totem-xine the default dvd player (if you decide to keep totem-gstreamer) in nautilus (the file manager for ubuntu) go to Edit->Preferences the Media Tab and under dvd select Open Movie Player (Xine)

I'm trying to do exactly this (I have both totem-xine and totem-gstreamer installed), but I don't have that option in the nautilus preferences - is there another way to make totem-xine the default dvd player?

Cheers :-)

[Edit: I'm trying to adjust the instructions here for my needs, but I'm a bit stuck at the moment... - [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)]

---

### Post by mc4man on 2008-04-26
> way to make totem-xine the default dvd player?
in terminal
```
sudo update-alternatives --config totem
``` choose 2

---

### Post by duckgoesoink on 2008-04-26
@mc4man - thanks a lot, that was much easier. :-)

---

### Post by ubuntu-freak on 2008-04-26
> **mc4man said:**
> in terminal
```
sudo update-alternatives --config totem
``` choose 2

 
+1
 
I keep forgetting about that command, it will come in handy now that both Totem Xine and Totem Gstreamer can be installed at the same time.
 
Nathan

---

