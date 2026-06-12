---
title: "[SOLVED] xmms in Hardy"
date: 2008-04-24
forum: Multimedia Software
---

### Post by Dave Otter on 2008-04-24
I want to be able to listen to shoutcast radio but when I try I get a message saying  UNABLE TO TUNE IN--dailed to execute child process "XMMS"
  no such file or directory.

Unable to load XMMS in Hardy

    Any solutions

---

### Post by JimmyHopkins on 2008-04-24
From what I can tell, maybe XMMS isn't playing because it has not been installed? XMMS isn't in add/remove programs in hardy. I had to do some digging to find a .deb for it (I use XMMS too).

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)
Try downloading the xmms.deb and install it. Sorry if I misunderstood your problem.

EDIT: I should add that that .deb is for i386 processors. If you need another build for a different processor, go to [https://launchpad.net/ubuntu/hardy/+source/xmms/](https://launchpad.net/ubuntu/hardy/+source/xmms/) and select the binary build for your processor.

---

### Post by kostkon on 2008-04-24
> **Dave Otter said:**
> I want to be able to listen to shoutcast radio but when I try I get a message saying  UNABLE TO TUNE IN--dailed to execute child process "XMMS"
  no such file or directory.

Unable to load XMMS in Hardy

    Any solutions
Just go to *Streamtuner*'s preferences and in the *Applications* tab change *XMMS* to *totem* or any other media player you are using. You do not necessarily need to install *XMMS* to make *Streamtuner* play web radio streams.

---

### Post by fbroce on 2008-04-24
Install realaudio (RealPlayer11GOLD.bin). Then go into preferences in streamtuner
(or whatever player your using) and replace xmms with realplay everwhere you see it.

Works fine on my AMD-64, Hardy.

fb

---

### Post by Novus on 2008-04-24
For some reason XMMS was removed during clean up :mad:
thanx for posting link to the deb.. I hope it'll work for me

edit:
It works fine for me ):P

btw, does anyone know where I can find a log of the packages deleted during cleanup? maybe more stuff was deleted that I still want :/

---

### Post by Linducker on 2008-04-24
Did you upgrade or install fresh.

---

### Post by Dave Otter on 2008-04-25
Many thanks to all who replied-and to Jimmy Hopkins for solution

---

### Post by disturbedite on 2008-04-25
i don't know if you guys did a clean install or not, but xmms was removed from hardy.  use audacious, its better any way.
discussion here:
[http://ubuntuforums.org/showthread.php?t=758942](http://ubuntuforums.org/showthread.php?t=758942)

---

### Post by Novus on 2008-04-25
Nice to be refered to a closed discussion. NO audacious isn't better. I downloaded just to check it out.. and guess if I got a surprise when I clicked the "I" in the main window.. (I meant to click the A but missed :D ) the precious audacious crashes and I start it again and all setting is reset to default.. audacious is better? IMHO we get a crap program thats still in alpha stage.

---

### Post by ofb on 2008-04-26
Thanks for the deb link. Very happy to have XMMS back.

Notes:

 - The "closed discussion" mentioned above has info on compiling from source around page 4, if people would like to do that. XMMS has a slighly newer 1.2.11 version out. I went with the 1.2.10 of the deb.

 - Audacious as a XMMS replacement... So far I have three issues with that, but maybe folks have soltions for them:

1. Animated effect when dragging player - it's not just irritating eyecandy on a lightweight player, but bogs badly on my slower machine. Where's the OFF switch?
2. Supposedly it uses Winamp skins, but they don't work. Do you have to change all the little BMP files to PNG?
3. Doesn't seem to have an equivalent for xmms-volnorm (gives all songs the same volume level).

Things like that are probably why some people don't agree that it's the same thing. And XMMS is noticeably lighter on the slower box. I'm very glad to have it back myself.

---

### Post by disturbedite on 2008-04-26
> **Novus said:**
> Nice to be refered to a closed discussion. NO audacious isn't better. I downloaded just to check it out.. and guess if I got a surprise when I clicked the "I" in the main window.. (I meant to click the A but missed :D ) the precious audacious crashes and I start it again and all setting is reset to default.. audacious is better? IMHO we get a crap program thats still in alpha stage.
there must be a problem on your system, it doesn't do that with anyone else.
and it wasn't a new program, it was forked from beep media player 2.5 years ago.  it is not in alpha.

---

### Post by Novus on 2008-04-26
> **disturbedite said:**
> there must be a problem on your system, it doesn't do that with anyone else.
and it wasn't a new program, it was forked from beep media player 2.5 years ago.  it is not in alpha.

Ok, then its a problem on both my desktop and laptop systems..
How I did:
Install audacious
Open audacious
View playlist
Chage skin to Refugee
click the "I"

Mission accomplished! audacious have crashed.. I guess the key is to have an empty playlist.

---

### Post by anjilslaire on 2008-04-26
Thanks, I've been lookin for XMMS as well. THe deb is great :)

---

### Post by eddietours on 2008-04-27
:guitar:wow you guys just rock l was looking for this thank to all

---

### Post by disturbedite on 2008-04-27
> **Novus said:**
> Ok, then its a problem on both my desktop and laptop systems..
How I did:
Install audacious
Open audacious
View playlist
Chage skin to Refugee
click the "I"

Mission accomplished! audacious have crashed.. I guess the key is to have an empty playlist.
well i'll be damned....i spoke too early.  i can actually reproduce this.  you have one thing right & one thing wrong though.
right: the key *is* an empty playlist. (it otherwise works as expected).
wrong: this is reproducible with any skin!

you might check to see if this is a known issue with audacious.  but regardless, don't check the info on a non-existent file or playlist!

i don't get any useful info when i do it though:
```
audacious amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
Segmentation fault
```

---

### Post by Blastomorpha on 2008-04-28
Why Xmms has been removed from Synaptic? However, thanks for the .deb in the first page, but was wondering about the libglib1.2 which need to be removed in order to install... will I have any problems running other apps?

---

### Post by ofb on 2008-04-28
Not sure what you mean. Hardy doesn't have libglib1.2, but uses libglib2.0-0. XMMS depends on libglib1.2ldbl, and I see the note for that lib says it conflicts with & replaces libglib1.2.

I'll guess some other app you installed put in libglib1.2, and it was replaced with libglib1.2ldbl when you put in XMMS.


I did some reading but never did find out why XMMS has been removed. There's opinion about obsolecense and lack of development, but the reps still have old barnacles like Sabre, so I dunno.

---

### Post by johnnylavah on 2008-04-28
is anyone else experiencing that the playlist does not minimize when you minimize the xmms player?

---

### Post by ofb on 2008-04-29
> **johnnylavah said:**
> is anyone else experiencing that the playlist does not minimize when you minimize the xmms player?

You mean minimize to toolbar? That works fine here on Hardy and Gusty. If you mean window shade mode, they were always separate for player and playlist.

Did you compile 1.2.11 or use 1.2.10 from the deb?

---

### Post by Fenrisulf on 2008-04-29
Found an easy guide to install XMMS in Hardy. Worked fine for me.
[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html]("http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html")

---

### Post by Blastomorpha on 2008-04-29
> **ofb said:**
> Not sure what you mean. Hardy doesn't have libglib1.2, but uses libglib2.0-0. XMMS depends on libglib1.2ldbl, and I see the note for that lib says it conflicts with & replaces libglib1.2.

I'll guess some other app you installed put in libglib1.2, and it was replaced with libglib1.2ldbl when you put in XMMS.


I did some reading but never did find out why XMMS has been removed. There's opinion about obsolecense and lack of development, but the reps still have old barnacles like Sabre, so I dunno.

Actually I didnt' install xmms yet, but I installed timidity. Maybe it's the "guilty one"?

---

### Post by johnnylavah on 2008-04-29
> **ofb said:**
> You mean minimize to toolbar? That works fine here on Hardy and Gusty. If you mean window shade mode, they were always separate for player and playlist.

Did you compile 1.2.11 or use 1.2.10 from the deb?

yes, minimize to tool bar.  when i select minimize on the player, only the player minimizes and the playlist stays up.  i am on hardy  -- this used to work fine on gusty.

i choose to keep xmms on my pc when performing the upgrade to hardy.  maybe i will uninstall xmms and reinstall it using the deb.

what version of xmms are you using?  1.2.11 or 1.2.10?  i currently have 1.2.10 but might be missing some files that i forgot to move over during the upgrade...

i will test this out tonight and report back on my findings.  thanks!

---

### Post by ofb on 2008-04-29
Blastomorpha - Could be. What I don't get is why you have libglib1.2 at all, since it's not in the Hardy package list or my Synaptic, and I've got all the usual repositories enabled. Did you upgrade to Hardy or do a fresh install? I did fresh. (I would have thought an upgrade would update libglib1.2 to libglib1.2ldbl, but perhaps not.)


johnnylavah - I'm using the 1.2.10 deb. Reason being only that it was simpler, that it has that nice Hardy page at launchpad which shows no Breaks or Conflicts, and I just use it for local music: there's no streaming so I'm not worried about having the very latest bug fixes.

I also like the deb because the installed XMMS shows up in Synaptic's list, which I'm hoping means Synaptic will take care of any dependencies/conflicts that appear later.

I can't find a changelog for 1.2.11 at xmms.org, so I don't know what they did, or when. The deb build is xmms_1.2.10+20070601-1build2_i386.deb. 

(Dates are worth knowing because the Ubuntu repository method tends to freeze on a version for the duration, but upgrade it with patches and bug fixes. Meaning Hardy would ship with ExampleApplication 1.5, and when ExampleApplication 2.0 comes out with new features + bug fixes, the Ubuntu maintainers will create a 1.5-1 with the 2.0 bug fixes, but not the features. They do that to make dealing with dependencies manageable. ExampleApplication 2.0 would be filed for inclusion with the next Ubuntu.)

I rather expect XMMS will show up as a backport project before long, so anyone with that repository enabled might check now and again to see if a new version shows up in their Synaptic.

---

### Post by Blastomorpha on 2008-04-29
I (succesfully :D ) upgraded from 7.10.
However I'm trying Ausdacios... really not that bad I thought, fast and simple like Xmms!

---

### Post by starchild7778 on 2008-05-03
Special thanks to Jimmy Hopkins for helping me get my XMMS player back in Hardy with his tip on page 1 of this thread!

---

### Post by ciamele on 2008-05-03
> **Fenrisulf said:**
> Found an easy guide to install XMMS in Hardy. Worked fine for me.
[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html]("http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html")

This worked very well for me. You have to open XMMS by hitting "alt+F2" and typing "xmms". I'd prefer to have an option under Applications > Sound & Video, or a desktop icon. I've posted a comment on the blog asking for instructions. Minus those instructions, it's still great to have the use of XMMS again.

---

### Post by ofb on 2008-05-03
ciamele, you can make your own menu items.

Go System > Preferences > Main Menu and select Add.  Or very similar; I'm on my Gutsy machine right now.

Note: the deb method creates the menu entry for XMMS.

---

### Post by bloodchilde on 2008-05-12
I just want to say that, as much as i like Audacious, XMMS is still better.
Audacious is full of bugs. It still crashes and sometimes it does it with deleting all your settings and kicking back to initial state, as when first installed. And that is FRUSTRATING. Furthermore, EQ is crap when compared to that of XMMS, and so is it's general sound. libmpg123 is 10x better than madplug. XMMS has that fat, warm natural sound, Audacious simply can't compare. Where XMMS' EQ adds color to the sound, the Audacious EQ takes it away. And one last, but probably most important thing: Audacious eats 17MB of RAM, while XMMS uses merely 3MB. Go figure. :rolleyes:


p.s. Thank you very much for the info. I was looking for that .deb too because i had problems compiling the source in hardy.

---

### Post by rabidninjawombat on 2008-05-23
Thanks for the link to the deb package.  After useing audacious i prefer XMMS,  if nothing else then for the smaller footprint

---

### Post by Kuoi on 2008-05-24
Thanks for the deb link from me too [-o<

I had only 1 problem with my upgrade too Hardy , and it was that I've lost XMMS to listen to Shoutcast radio trough Streamtuner.

I've tried about all media players , but not 1 come close.
Just 1 maybe ... Audacious , which I was using the last couple of days.
That comes very close , but I must say , I only use Audacious ( and now XMMS )  to listen to radio , nothing else.

Thanks again for the deb file.

Kuoi

---

### Post by nicedude on 2008-05-28
Thanks Jimmy as it worked quite easily with my 32 Bit Hardy and I wasn't ready to give up my XMMS ( if it aint broke don't fix it :-) ) and you saved me from having to compile it myself so thanks a bunch.

To all who read this, The deb installer works like a charm and will install the other needed packages for you successfully as well.

---

### Post by trapik on 2008-06-17
thanks too JimmyHopkins :guitar:

---

### Post by Bungo Pony on 2008-06-17
XMMS was one of the first things I installed when I moved to Hardy. Can't remember what I did to install it, but I'm also having the minimize player issue as well. However, I don't care - I LOVE my XMMS!

Audacious is a heap of junk. When it took around two minutes to load my large playlist, I knew it wasn't for me. I use my playlists extensively, and I can't be bothered to wait minutes for them to load.

---

### Post by markbuntu on 2008-06-17
I have been wanting to get streamtuner working for weeks. Audacious just did not blow my dress up if you know what I mean and totem is not really a good streaming music player and rythmbox just would not work with streamtuner though it does work with tunapie, sort of. Now, I can use streamtuner again

Thank you thank you thank you!!!

PS. I can confirm this also works on 64 bit amd64 Hardy.  A small dependency issue with libglib1.2 but quickly worked out. Once again, thanks

I have both386i and amd64 on separate hard drives and try stuff out on both.

---

### Post by markbuntu on 2008-06-21
Well, it works in amd64 once you straigten out the problem with the debs. The problem libs can be found here. I ran Gdebi and it stopped with a deb issue between ligglib1.2 and libglibl.dbl 

[https://launchpad.net/ubuntu/hardy/amd64/libglib1.2-dev/1.2.10-19build1](https://launchpad.net/ubuntu/hardy/amd64/libglib1.2-dev/1.2.10-19build1)

[https://launchpad.net/ubuntu/hardy/amd64/libglib1.2ldbl](https://launchpad.net/ubuntu/hardy/amd64/libglib1.2ldbl)

 I am not sure, I had them on my Desktop just in case and the install did not work, but I removed ligglibdbl with synaptic and then ran 

apt-get install -f 

or whatever it said when the install failed and it installed some libs. Then I ran:

apt-get remove ligglibdbl 

and installed libglib1.2-dev with Gdebi 

and then tried to install xmms again and it worked.

Something like that anyway. It was late last night. But anyway, xmms works in both 386i and amd64 Yay!

---

### Post by yakkeh on 2008-06-27
> **Novus said:**
> Nice to be refered to a closed discussion. NO audacious isn't better. I downloaded just to check it out.. and guess if I got a surprise when I clicked the "I" in the main window.. (I meant to click the A but missed :D ) the precious audacious crashes and I start it again and all setting is reset to default.. audacious is better? IMHO we get a crap program thats still in alpha stage.

My thoughts exactly! XMMS rules :) The I crashes audacious for me as well. I didn't even bother restarting it... even totem movie player works way better for my mp3z :guitar:

But besides all that, I am really digusted by people telling other people what to use. It goes in against everything that Linux/GNU stands for: freedom to do whatever you want with your computer, even if it means using or installing deprecated software!
If someone wants to use XMMS and wants to know how this is done, don't explain how to get other programs working, don't explain what advantages other programs have over the one he wants, don't tell how bad this program is... that is all OFF TOPIC. If you don't want to contribute to the topic, just STFU.

Audacious may be promising, but it's not at all in the same steady state that XMMS was/is and until there is no good successor, it shouldn't be taken out of the repository, even if there is no more development being done to it.

But then again, that's just my personal opinion :popcorn:

---

### Post by markbuntu on 2008-06-27
The only problem I have with xmms is that it hogs the sound. Does anyone know how to configure xmms so it will let other apps also use the sound?

I have it running with alsa right now but I wonder if it work with pulseaudio and if so, how to set it up?

Never mind. I figured it does since I changed around my sound setup again for the fortyzillionth time. I think this one is a winner.

This time I have everything in Sound set to ALSA and the ALSA default sound card set to pulseaudio and ALSA set as the default driver in libao.conf and pulseaudio disabled from loading at boot with Boot Manager. Somehow, pulse is still loading, probably with hal, but it is using the ALSA sinks and sources.

 So, PA is using alsa sinks and sources and ALSA is using PA Manager for multiple sound inputs which PA directs to the ALSA sinks. Circular, I know, and you would expect that this would not work but it does. XMMS is using the alsa-xmms plugin and rythmbox is using the alsa-rythmbox plugin and they are both playing through PA Manager right now. I can get a really weird delay/echo effect when I have them both playing the same stream.

---

