---
title: "wildlife photos via webcam - what software?"
date: 2011-05-01
forum: Multimedia Software
---

### Post by grey1beard on 2011-05-01
With a rare bird visitor to my small pond, I thought it would be straightforward to take a photo via my Quickcam F2500 on the Toshiba Satellite laptop, using Cheese.
Unfortunately there is a 3 second delay between hitting the button and the software taking the picture, by which time my visitor could be down the road.

Q1. Is there a way round this in Cheese ? 

I tried using Camorama Webcam Viewer, which takes instant shots, but the colour rendering is way off (Robin Bluebreast !)and the controls don't seem to have any effect in either my laptop with 8.04 or my desktop with 10.10.

(The photo is also very low resolution in Camorama)

Q.2 Are there any other programmes that you would recommend for this sort of requirement, ie instant pic, and reasonable size and colour controls, as I can't find any in the Software Center ?

John

---

### Post by Dingo_aus on 2011-05-01
I use the software "motion" for surveillance:

[http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome)

It is easy to use once you realise that the motion.conf texdt file controls everything and there is no way around configuring it via editing that file.

---

### Post by grey1beard on 2011-05-01
Hi Dingo, and thanks for the link.
It looks even better than I than I was thinking of, so the challenge for me is to get my old grey cells round the config !

John

---

### Post by Dingo_aus on 2011-05-01
I've got a few notes on how I use it here:

[http://adventuresinsilicon.blogspot.com/2011/03/pandaboard-using-webcam-as-security.html](http://adventuresinsilicon.blogspot.com/2011/03/pandaboard-using-webcam-as-security.html)

and

[http://elinux.org/BeagleBoardUbuntu#Motion](http://elinux.org/BeagleBoardUbuntu#Motion)

The config is the same whether you are running it on Ubuntu on a desktop PC or an embedded PC like I am.

It is pretty easy once you've done it once. If you get stuck post back here and I'll upload my config. If you get really stuck I'm happy to Skype to fix it but if we can do it on the boards here it will help everyone.

---

### Post by Dingo_aus on 2011-05-01
Oh btw "motion" is available from the normal repositories for download.The key file is then at:

/etc/motion/motion.conf 

or

/etc/motion.conf

This is me guessing from the top of my head. I can check it if you need me to.

---

### Post by grey1beard on 2011-05-01
Thanks Dingo.
I'm wading through the guide at the moment, in the Summer House next to the pond.
As I can't replenish the beer supply till tomorrow, I expect it may be a couple of days experimenting before I come back with my first sticking point !
I've got my digital camera here with me, just in case my little friend turns up - usually about 6pm for a quick drink - so I have the afternoon to try to set up.
John
PS just caught your 2nd mail - yes, I used the package manager to download and install, so I'm on the way.

---

### Post by no2498 on 2011-05-01
if the color is still off try this program v4lucp you can change things in it

it comes up in/under system / preferences as video4linux control panel

---

### Post by grey1beard on 2011-05-01
Hi Dingo,
Well it only took me about three hours to realise that I wasn't going to get anywhere re editing the provided config file.

I've done a lot of reading across several sites, and I have a grasp of what the software needs to get it set up, but I've got too little background knowledge to get through it.
For example, my Terminal skills are pretty basic, and not used frequently, so I tend to forget how to's quickly. 
Several problems ahead. I've found the example config, motion.conf, which curiously says on its first line "Rename this file motion.conf", and with what seems to be all the lines commented out. 
I tried to copy/paste a new file to edit, leaving the original intact with the intention of renaming that "oldmotion.conf", but it told me I didn't have permissions.
I know I've been there before, but I forget how to, so that seems to me my first step, change permissions for the motion.conf file ?
Then I've no idea what lines to uncomment to get the default settings to try. 

Perhaps it would be a kindness if you were to post an example for me to try, then modify !

My next hurdle will be starting it in Terminal. Just type <motion run> ?

Then I see that I need to open a web browser to see in real time what the camera is seeing. Not at all sure how I do that. Guess I have to create some sort of local address (?) for it, then open Firefox and type in the camera's url ?

Time to get back to the pond with the digital, just in case it's early.
Thanks again for your help,
John

---

### Post by no2498 on 2011-05-01
motion saves its files to your home folder
it did for me anyway

---

### Post by grey1beard on 2011-05-01
> **no2498 said:**
> if the color is still off try this program v4lucp you can change things in it

it comes up in/under system / preferences as video4linux control panel


Hi No.2498, which program are you referring to here, motion, cheese, or camorama, or is it one that can 'edit'color in all of them ?
Many thanks,
John

---

### Post by no2498 on 2011-05-02
it helps them all
it has a preview window

not sure if you need to stop motion first tho
you may need to

---

