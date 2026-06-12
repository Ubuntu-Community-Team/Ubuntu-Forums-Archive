---
title: "Cannot  see my iPod with Rhythmbox"
date: 2009-05-26
forum: Multimedia Software
---

### Post by Lakeside5 on 2009-05-26
Ok, so I am starting to think there is something wrong with my usb ports on my computer (I'm running Hardy Heron server edition.) First, I cannot see my external hardrive when it is plugged into usb port, and I can't see a new flash drive either, and now, I tried to put music on my iPod, and decided to use ubuntu's rhythmbox which is on here. When I plugged the iPod into the computer, it asked what I wanted to open it with and I chose rhythmbox, but it does not show up there. I don't know how to put music on my iPod.

---

### Post by Boondoklife on 2009-05-26
> **Lakeside5 said:**
> Ok, so I am starting to think there is something wrong with my usb ports on my computer (I'm running Hardy Heron server edition.) First, I cannot see my external hardrive when it is plugged into usb port, and I can't see a new flash drive either, and now, I tried to put music on my iPod, and decided to use ubuntu's rhythmbox which is on here. When I plugged the iPod into the computer, it asked what I wanted to open it with and I chose rhythmbox, but it does not show up there. I don't know how to put music on my iPod.

Ok well the good news is your usb is working as it seen you plugged in your ipod!!!
Now what type of ipod is it and what generation?
Secondly check to make sure the ipod plugin is turned on in rhythmbox.

If all else fails try to install hipo "apt-get install hipo" and see if it can see your ipod.

---

### Post by Lakeside5 on 2009-05-26
Thanks for the help maletek. I'm not sure how to  turn on the iPod plugin in Rhtyhmbox, so I ran the code you gave me i terminal, and it looked like it installed some stuff, but I do not see my iPod in Rhytmbox still.

---

### Post by Boondoklife on 2009-05-26
hmm looks like my post got cut off,

as far as the plugin in rythmbox,
click Edit -> Plugin
then make sure the ipod plugin is checked

the app you install would be located under the menu -> Applications -> sound & video -> hipo ipod management tool.

the hipo app will let you see the ipod if it is connected and load it up.

---

### Post by Lakeside5 on 2009-05-26
I see that 'portable players-iPod' is checked in Rhythmbox plugins, but when I check the hipo iPod management tool, it says 'no iPod found' :( grrrr  lol

---

### Post by Boondoklife on 2009-05-26
> **Lakeside5 said:**
> I see that 'portable players-iPod' is checked in Rhythmbox plugins, but when I check the hipo iPod management tool, it says 'no iPod found' :( grrrr  lol

hmm what type of ipod is it, model and generation please.

---

### Post by Lakeside5 on 2009-05-26
It is an iPod touch, 8GB, not that old.

---

### Post by Peperm1nt on 2010-01-26
OK, i think i can help you. But be warned im no linux God or anything, just learning like you. I spent all night last night trying to figure it out, and this is what i did for a iPod 8GB Touch. idk if it is 3rd 4th or w/e i kno it works ;) , this should work for ALL iPods.

IMPORTANT STEP:
Ok. First you need to be able to "see" the iPod. When you plug it in, does your computer recognize it? You will kno this when your computer will bring up an icon on the desktop stating the name of the iPod. Also, you can check by going to places>computer and you should be able to see it there. Also, you can go into the iPod from places>computer and see the folders and such on the iPod.

If you can NOT see the ipod in either area you need to download gtkpod or find a way to MOUNT your iPod. I honestly dont remember that part last night for you, but im pretty sure that downloading gtkpod fixed that. Ill research and post more later. i think gtkpod just had the driver or w/e to recognize my iPod.

Once you have did this, open rhythmbox. Now this is the problem I HAD. Ever since I've installed ubuntu 9.10 to my system, I've always used rhythmbox. I personally like it better than amarok and such. ON THE LEFT SIDE of the screen i never saw the sources pane. That entire list was hidden from me. I had to manually drag that window side to show a playlist queue then on the top side there is another "drag" icon on my mouse and i had to drag that down to show a sources pane. Once you drag that down, you should be able to see your iPod. When you go into the iPod from rhythmbox, you will see all the songs on your iPod to delete and as such. When you add songs to the iPod this way, you will see a progress bar on the bottom right of your screen. THat is all i can figure out thus far is to move music. I believe to move pictures, you have to manually move picture in the file browser screens. from you pictures folder to the iPod folder. 

Hope this helps,
Peperm1nt

EDIT:

Make sure the iPod checkbox is checked in the rhythmbox plugins

---

