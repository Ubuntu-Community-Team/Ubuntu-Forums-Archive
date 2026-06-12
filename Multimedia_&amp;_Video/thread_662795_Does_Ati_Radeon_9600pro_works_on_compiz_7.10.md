---
title: "Does Ati Radeon 9600pro works on compiz 7.10?"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by juliahn on 2008-01-09
hi guys..! I'm really tired of searching and looking up information about the compatibility between my graphic card (asus ati radeon 9600pro agp 8x) and ubuntu 7.10.

I tried ubuntu mainly because the famous "cube" and screen effects thats  ubuntu brings to us..


i've already installed some drivers called "fglrx"

i think that are already well installed.., but when i try to customize the effects on "appearance" menu, i got this error...

"The Composite extension is not available"

this error comes out when i click "extra, custom or normal"


I really think that my graphic card has 3d.

im really noob at gnu's world and i'll appretiate if you are detailed and kind with me... :)

sorry for my english, im argentinian.. i'll be hoping your reply.

---

### Post by CypherHackz on 2008-01-09
just use [envy]("http://albertomilone.com/nvidia_scripts1.html"). it helps you from doing the hard work. :p

---

### Post by juliahn on 2008-01-09
i have seen this link before, but the author that put it said "use it at your own risk"
so then i close the window.. xD

i'll try it and as soon as i can i'll let you know.. ;)

---

### Post by CypherHackz on 2008-01-09
but it really helps me. before this i was having problem to setup ubuntu to make it works with my graphic card ati radeon hd2600xt. but when i use envy, everything is smooth and run perfectly. :)

---

### Post by juliahn on 2008-01-09
do i have to restart the pc? or works without restarting?

i've restarted and i am still having the same problem..

any other suggestion?

---

### Post by juliahn on 2008-01-09
wooowww meeenn this is really the shitt!!


it's working finee at the moment!!

i've personalised the cube and enabled but i dk how to open it.. :P

---

### Post by CypherHackz on 2008-01-09
ha3. i told you that it will work! :p

to see the cube effect, you need to press ctrl+alt+left-click and move your mouse. i am not sure if it will work or not because im using another settings. :) i use ctrl+alt+spacebar and move the mouse to see the cube.

---

### Post by Gvaz on 2008-01-09
I have also done this route, however, I cannot find anything with which to "personalize the cube" nor does "ctrl+alt+left mouse" and moving it just leaves a drag box.

Is there something I might be missing here?

---

### Post by CypherHackz on 2008-01-09
i think you guys does not install yet the Advanced Desktop Effects Settings.

To do it, open up a Terminal and enter this command,

```
sudo aptitude install compizconfig-settings-manager
```

This will install the compiz settings manager. After the installation is done, go to System > Preferences > Advanced Desktop Effects Settings. And then set anything you want from there.

Hope this helps.

---

### Post by Gvaz on 2008-01-09
> **CypherHackz said:**
> i think you guys does not install yet the Advanced Desktop Effects Settings.

To do it, open up a Terminal and enter this command,

```
sudo aptitude install compizconfig-settings-manager
```

This will install the compiz settings manager. After the installation is done, go to System > Preferences > Advanced Desktop Effects Settings. And then set anything you want from there.

Hope this helps.

I did this, but I just have two workspaces, and it flips like a page, how do I add more of those workspaces so it shows up as a cube?

---

### Post by CypherHackz on 2008-01-09
i see...

if like that, right-click at the workspace at the lower right of your screen and choose Preferences. In the dialog box, set 4 to columns and 1 for rows. then Close.

Now try flipping the cube. ;)

---

### Post by juliahn on 2008-01-12
hi guys, it's me again..

now, i've set up the cube.. it all works fine, and also i've settled some keys customization for the cube...

now, since i've installed this drivers for my 9600 pro i cannot see any video.. i can see them from web but not from my pc...  

i opened i video i have and it shows all dark.. (black screen), but when i'm resizing the window to see it bigger, the image appears, but when i unclick again.. it comes the black screen again..

any suggestion?

---

### Post by CypherHackz on 2008-01-12
i think you need to set the output setting. in the video player, go to options/preferences , find the output setting and choose X11 from the selection if I am not wrong.

-cypher.

---

### Post by juliahn on 2008-01-14
thx 4 answering..

now, i've various X11 to apply

i'm sending an screenshots for you to see which do i have to apply for


[IMG]http://i9.tinypic.com/731r6op.png[/IMG]

thx again

---

### Post by juliahn on 2008-02-02
does anybody knows?

---

