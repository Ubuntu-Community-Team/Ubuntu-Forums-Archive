---
title: "Ubuntu 6.06 LTS Screen Resolution Problems"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by nicenick on 2007-06-02
OK, I hnow have to post using my wifes MS XP computer because my Ubuntu has crashed beyond all use.

1. I have 2 different help requests in already. 1 is in launchpad something, 1 is in this forum, I don't know the difference on who is running each. but let me recap my problem and the new twists that have occured.

I used Ubuntu perfectly for 6 months, then last week my screen resolutions 'messed up' The only picture I could get was HUGE, it was about 4 screens wide, every other resolution was a Black screen.  The first Ubuntu 'splash screen' was perfect, then when asking me to login, the screen went black, but [ctrl] [alt] [+] would give me a readable screen, althougt HUGE. I have a PCChips motherboard A31G, built in SIS VGA , with a generic Optiquest Q41 14" monitor (ancient but works).

My [System] [Preferences] [Screen Resolution]  shows 3 resolution, 2 give balck screens and only the higest give me the HUGE screen.  The refresh rate was 0 and could not be changed.
The , reading the forums, someone added refresh rate 30 - 62 to their X11-xorg.conf file and resolved a similar problem. However, after adding thes line, and rebooting, I could never get into Ubunt again. When asked for the user and password, IThe screen goes balck and I immediately get sent back to the Login screen.

Now, continuting , I started ubunt in the Safe Graphics mode and get presented with what looks like a terminal but isn't. I get
nick@nick-home:~$
What is the [~$] because it is not my terminal and I can't run gedit or sudo or anything else that I can understand to try to undo what I have already done.  I made a backup of X11/orog.conf, but I can't 1. get into ubuntu, 2. use this terminal looking thing to execute sudo gedit /ext/X11/oxrg.confg.

What do I do next. 

Help, Help, Help

If you look about 6days ago your can find my (nicenick) post    opys of my xrg.confg and kjy lspci, sudo lshw -c video files.  but please do not ask me to repost, I CAN'T get Ubunt to boot or find a method for me to access any of these commands again.

Frustrated in Ohio,

niice nick

---

