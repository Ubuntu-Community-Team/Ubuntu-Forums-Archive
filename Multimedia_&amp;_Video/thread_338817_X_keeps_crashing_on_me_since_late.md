---
title: "X keeps crashing on me since late"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by jaywhy13 on 2007-01-15
I'm not sure what's happening to my X.... the only changes I can recall doing recetly so far are the following...

1. Installed the latest driver from ATI's site
2. Upgraded my version of the svn repos for beryl  (dist-upgrade)
3. Updated the xserver-xorg-core module coz there was an update for it... (dist-upgrade)

X crashes on me very regularly now and frankly upsetting is merely the word... am pissed now... need som help...

PLZZZZZ ne clue what could be happenin?

Only one other person in Beryl's forum said they are experiencin the same problem...
How can I go about pinpointing what exactly is the problem? 

I don't think I can do nething about reverting back the version of xserver-xorg-core since I dist-upgraded... if there's a way... al try if someone'll point me in da right direction

I've tried changing from the svn version of beryl to the stable one... no difference.

Last am gonna try reinstalling ma old driver and see what happens

---

### Post by jaywhy13 on 2007-01-15
can anyone PLZZZ help, this problem is nothing short of ANNOYIN

---

### Post by sgx on 2007-01-16
Reinstall, enjoy for awhile, and then buy an nvidia card, one googlesearched to be working
with your distro, and follow the nvidia readme from their driver download
page...their instructions work, when precisely followed. Linux has no umpires. ATI seem unwilling to devote more than a skeleton krew to their drivers, and you are their latest victim. But windoze is their business...so be it. Let freedom reign.
I hate to say it, but from reading these forums, it appears
Ubuntu is moving way too fast, and failing to get the basics of audio and video in order. Don't be afraid to go with another distro for awhile, Mandriva, Mepis, Knoppix, Fedora, Suse, they all are linux under the hood, each with its own host of raving, drooling fanboys, shouting  'kill the troll who  thinks ooooooouuuurrrrrrrrrr way is not the best" My guess is your ATI card is not one of the lucky few ones supported adequately,
and legacy cards are being dumped altogether. An older driver may work fine for  your card. But google search, and review...the smallest neglected  step sends you into the xless void...took me about seven times to fathom nvidias instructions, and then colate them with editing xorg.config, getting the right runlevel, typing accurately while ranting and raving...I'm sure many feel your pain... good luck!

---

### Post by jaywhy13 on 2007-01-17
> **sgx said:**
> Reinstall, enjoy for awhile, and then buy an nvidia card, one googlesearched to be working
with your distro, and follow the nvidia readme from their driver download
page...their instructions work, when precisely followed. Linux has no umpires. ATI seem unwilling to devote more than a skeleton krew to their drivers, and you are their latest victim. But windoze is their business...so be it. Let freedom reign.
I hate to say it, but from reading these forums, it appears
Ubuntu is moving way too fast, and failing to get the basics of audio and video in order. Don't be afraid to go with another distro for awhile, Mandriva, Mepis, Knoppix, Fedora, Suse, they all are linux under the hood, each with its own host of raving, drooling fanboys, shouting  'kill the troll who  thinks ooooooouuuurrrrrrrrrr way is not the best" My guess is your ATI card is not one of the lucky few ones supported adequately,
and legacy cards are being dumped altogether. An older driver may work fine for  your card. But google search, and review...the smallest neglected  step sends you into the xless void...took me about seven times to fathom nvidias instructions, and then colate them with editing xorg.config, getting the right runlevel, typing accurately while ranting and raving...I'm sure many feel your pain... good luck!

Trust me when I tell you that if I could get an nVidia card I would... I have a dell laptop... i've been cursing ATI since like forever man... I learnt about ATI and the bs they dish 2 linux before I really started learning and using linux... so it does hurt!!!! Neways... am really thinkin of tryin out another distro... jus can't bother coz it's gon b tiresome reinstalling and all dem stuff and backin up ma filez and stuff... Am thinkin I wanna check out a distro that doesn't giv crap about propierty stuff that comes with more stuff on it... most of da plugins so I don't hav 2 go through the hassle... it's really not convenient now, coz a got a few major projects working on.

I was thinkin of tryin out DreamLinux... what you think? Suse, I think I might retry... I gave Suse a shot already and wasn't impressed with their pkg manager... wasn't workin for me...

---

### Post by sgx on 2007-01-19
> **jaywhy13 said:**
> Trust me when I tell you that if I could get an nVidia card I would... I have a dell laptop... i've been cursing ATI since like forever man... I learnt about ATI and the bs they dish 2 linux before I really started learning and using linux... so it does hurt!!!! Neways... am really thinkin of tryin out another distro... jus can't bother coz it's gon b tiresome reinstalling and all dem stuff and backin up ma filez and stuff... Am thinkin I wanna check out a distro that doesn't giv crap about propierty stuff that comes with more stuff on it... most of da plugins so I don't hav 2 go through the hassle... it's really not convenient now, coz a got a few major projects working on.

I was thinkin of tryin out DreamLinux... what you think? Suse, I think I might retry... I gave Suse a shot already and wasn't impressed with their pkg manager... wasn't workin for me...

Try Mepis, Mandriva Dynebolic and Knoppix live cds, and make a
separate /home partition that you can save un-reformatted during future 
reinstall...maybe get a $23 usb hardisk adaptor case, take the innards out, and hook up a cheap cd/dvd writer for a backup system. Mandriva has the easiest and best disk formatting utility, you can power down after its done, aborting a Mandriva Install, then your distro of choice can use what Mandriva made...it also has the most precise install package selection, while knoppix/dynebolic have great hardware detection, and Mepis is lucky, in that so much that causes teeth-grinding/hair-pulling in other debian variants, works so smoothly...
I have a Mepis/Ubuntu hybrid setup for playing windoze vst instruments
and use many divergent repositories, though I almost never change a system that works, creating my own good luck...hope you have some too...

---

