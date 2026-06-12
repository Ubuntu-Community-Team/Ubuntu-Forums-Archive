---
title: "streaming videos to x-box 360 (Twonky?)"
date: 2009-05-28
forum: Multimedia Software
---

### Post by clairefun on 2009-05-28
Hi, I'm hoping somebody can help me as this is starting to drive me crazy :)

I used to watch my videos through my 360 using windows media connect software, and I'm missing it in Linux. I'm trialing twonky media but although my mp3s show up, when I go into the videos>Twonkymedia folder it just says 'No videos found' and gives me no other options. I've looked at a few of the other bits of software but they all seem way too complicated to set up - I've only had linux a little while and don't really understand the terminal, I've been installing everything via synaptic or add/remove programs. All the 'easy' guides keep telling me to type this then check these random letters, etc. I'm happy to use Twonky (and pay for it) if only it would work properly...

I hav my videos in my home/videos folder, would that make *any* difference? Or has anyone had this issue and worked out what causes it and how to get around it? Or know of any other software that's as easy as Twonkymedia to use if you know nothing about linux?

Oh I CAN browse my videos in the online twonky browser, and they play on my computer fine. Just the X-box 360 doesn't see them, and I don't know why!?!

---

### Post by infallible on 2009-06-09
check your firewall. I'm just now setting mine up for twonky, so here's the step-by-step:

install twonkymediaserver, set up directories, etc. confirm with web based media browser.

Install firestarter, a front end for the already installed firewall. Start it via the new menu icon, go through the wizard, leave the window open. things get funky for mine when I X out of the firestarter window, but it stays running if you click its icon on the top.

Turn on the xbox. You should see a few requests in the events tab from an IP in your local network, starting with 192. or 172. or even 10. You can confirm you are seeing the 360 by looking at 'Configure Network' under network settins in the system settings section of the xbox. You'll see the xbox's IP address there.

Right-click that IP address in the events tab of firestarter and select 'allow connections from source'. Now the computer knows the xbox is 'safe.'

Browse through the xbox video library and enjoy!

---

