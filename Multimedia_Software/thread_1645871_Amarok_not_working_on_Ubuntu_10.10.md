---
title: "Amarok not working on Ubuntu 10.10"
date: 2010-12-15
forum: Multimedia Software
---

### Post by Ederico on 2010-12-15
Dear all,

I just made the switch back to Ubuntu from Kubuntu. Now I'm having problems running my favourite KDE app, that's Amarok.

Amarok regularly scans my collection, no problems with that. When I try and play any tracks they're not playing and Amarok scrolls through the playlist without playing anything. No error messages are displayed either (although I remember once I got some message related to phonon).

Anyone have any idea what the problem could be and how I could get Amarok running on Ubuntu 10.10?

Regards,
Ederico.

---

### Post by Linyx on 2010-12-15
> **Ederico said:**
> Dear all,

I just made the switch back to Ubuntu from Kubuntu. Now I'm having problems running my favourite KDE app, that's Amarok.

Amarok regularly scans my collection, no problems with that. When I try and play any tracks they're not playing and Amarok scrolls through the playlist without playing anything. No error messages are displayed either (although I remember once I got some message related to phonon).

Anyone have any idea what the problem could be and how I could get Amarok running on Ubuntu 10.10?

Regards,
Ederico.
[SIZE="2"]Not sure what the Problem is...somedays ago, i had try to run Amarok on Lucid,but same issue, i think its not suitable for Gnome-Enviroment, 
You can try the*** Alternative*** of it > ***Rhythmbox***[/SIZE]

---

### Post by Ederico on 2011-01-01
Ok, I tried Rhytmbox, it does play music. I also tried Listen and Exaile. They don't compare with Amarok unfortunately. I know I had Amarok working in GNOME in the past, but I forgot what I did. :(

---

### Post by mc4man on 2011-01-01
Don't use amarok2 here but i'd first start by making sure that libxine1-ffmpeg is installed

---

### Post by Ederico on 2011-01-01
> **mc4man said:**
> Don't use amarok2 here but i'd first start by making sure that libxine1-ffmpeg is installed
That was it! Thanks a lot mc4man!

By the way, Happy New Year!

---

### Post by NRG4WAR on 2011-02-15
Ok first off i would just like to stress i am a TOTAL linux/ubuntu noob! BUT for anybody else who may stumble across this thread because your Amarok wont play your music in ubuntu/kubuntu 10.10 then i have a solution that worked perfectly for me. I have to stress though that this was done on UBUNTU 10.10 - So being a linux noob, I have no idea if this method is backwards compatible with earlier Ubuntu/Kubuntu versions.


[LIST=1]
[*]**Obviously first off download amarok through ubuntu software center.**
[*]**Load up amarok. Drop all of the music files you want to play into amarok.**
[*]**Now when you click play it may just scroll through ALL your music files rapidly and not play a single thing. DO NOT load your music files into amarok twice like I did or you WILL just have a ton of duplicate tracks**
[*]**Close amarok completely (you may need to right click the amarok icon in the top right and then click close to kill the app 100%)**
[*][B]Open a Terminal Window and input the following code (copy/paste for speed)
[/B]
[/LIST]

sudo apt-get install amarok kubuntu-restricted-extras


[B]Now you will get a long list of output followed by a section that requires you inputting Y/N to continue instillation. press Y then hit enter.

Next you will get a micrsoft license agreement appear. You have to hold the down key and scroll aaaaaaaall the way to the bottom until the <OK> button is highlighted - Hit enter to finalize and accept license agreement.

Exit your Terminal Window - Load up Amarok again and your music should play 100% with no hiccups, errors, system crashes or demons flying out of your computer. :KS

[/B]As i stated before - I am a linux noob so if this does not work, i really would not be qualified to answer any follow up questions as to why it wont work for you.

I would however appreciate if somebody could let me know if this was a success for them - more out of curiosity - not to feed my ego :) Feel free to copy and paste this into other forums or areas of this forum as I am kinda lost trying to find the right place for this post, so i figured i would just drop it at the bottom of the original posting.

Hope it goes well guys and girls - _**NRG**_

---

### Post by greybot on 2011-02-16
Had the same error as you and got it working following your instructions. Many thanks :KS

---

### Post by NRG4WAR on 2011-02-16
> **greybot said:**
> Had the same error as you and got it working following your instructions. Many thanks :KS

Brilliant! Thanks for the feedback GreyBot - Its good to know I didnt blow up somebodies computer and it's even better to know it worked for others :popcorn:
_**NRG**_

---

