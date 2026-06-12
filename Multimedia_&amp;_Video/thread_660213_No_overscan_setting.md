---
title: "No overscan setting"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by dysphasi on 2008-01-06
I'm a tad confused here. 

I'm running a VAIO C2S laptop with Intel 945GM graphics under gutsy, unfortunately a dual head setup is not possible and I have to use xrandr.

Basically, I want an extended desktop, I achieve this as follows:
```

xrandr --output TV --right-of LVDS --mode 640x480 --set TV_FORMAT PAL

```

However, the picture on the tv doesn't fill the screen properly. I get this same problem on my desktop pc with an NVIDIA card, however the nvidia settings easily allow me to increase the 'overscan' setting.

How can I achieve a similar 'overscan' from my laptop's card to the tv? 

Thank you in advance people!

(nb...I've tried using all the available resolutions, this doesn't make a difference)

---

### Post by dysphasi on 2008-01-09
Is there no way of achieving some kind of overscan using xrandr at all?

---

### Post by qntal on 2008-01-11
it seems we're the only 3 persons in the world who cares about overscan with intel 945 :lolflag:

---

### Post by dysphasi on 2008-01-12
You counting me as two ::roll: ...lol didn't see the other chap posting, so there are 3 of us...c'mon folks, no-one any idea?

It's odd, so many laptops and mobos come with integrated intel graphics, plenty of people have media center setups and I've not found a single machine that just works out of the box under ubuntu in dual display mode, I always need to tweak at least the overscan (when I can!)

---

### Post by mrsteveman1 on 2008-02-27
I seem to remember that at least as recently as late 2007, the intel driver had no option to control the overscan on the TV output.

IE the driver itself didn't provide a way to do this. Normally it would be implemented as an extra option line in xorg.conf but I have read every bit of documentation for the driver i can find and there simply isn't an option for overscan right now.

---

### Post by dysphasi on 2008-02-27
Using it right now on windows, have done since I've had the computer, admittedly it's not so tweakable as nvidia is, but it allows for the screen to be nicely stretched across the tv screen without huge black borders.....so hopefully it's just a matter of time going by what you say.

Unfortunately it's nigh on impossible to get a decent dual screen setup in linux even on my nvidia machine. 

Alongside shutting down issues on both computers I've tried and tried, but with regret threw in the towel and have gone back to windows...at least it works. Maybe I'll be able to return to linux come ubuntu 8.04.

---

### Post by gcpete on 2008-05-16
It is possible with a little work. You have to use [http://wilmer.gaast.net/blog/archives/34-Change-Intel-X.org-TV-Out-margins.html]("http://wilmer.gaast.net/blog/archives/34-Change-Intel-X.org-TV-Out-margins.html"). If you don't feel like compiling it I have made a deb which works on 7.10 and 8.04 which is attached to the end of this post. Download and double click to install. 

Now follow these instructions from the read me what I wrote!!

This is a command line tool that allows you to get rid of the annoying black borders you often get around the TV output of your intel video card as used in many laptops. It does not make any permanent changes to your X configuration and so has to be run each time you want to correct your TV picture.

First you need to work out what values work for you. Connect your TV and activate the output, eg with a button combo or xrandr command (I guess you can get the picture on the TV or you would not know you had annoying black lines!

Now open up a terminal (Applications -> Accessories -> Terminal) and enter

```
xtvmargin TOP -set 17
xrandr --output TV --mode 640x480
xrandr --output TV --mode 1024x768
```

The last to are needed to activate the changes you made. Now look at the TV picture and see how close to the top the menu is, repeat the process adjusting the value until you find a position you like. Now repeat the process for TOP BOTTOM LEFT RIGHT. For the record my values are

```
xtvmargin TOP -set 22
xtvmargin BOTTOM -set 40
xtvmargin LEFT -set 20
xtvmargin RIGHT -set 15
```

Once you have found values that work why not make a small bash script to allow you to configure the TV output easily. Copy and paste the following into a new file, substituting the values given for the ones you found above.



```
xtvmargin TOP -set 22
xtvmargin BOTTOM -set 40
xtvmargin LEFT -set 20
xtvmargin RIGHT -set 15
xrandr --output TV --mode 640x480
xrandr --output TV --mode 1024x768
```


Save the file. Now using nautilus right click on the files icon select properties then the permissions tab and tick the allow file to be executed box. Close the properties window. Now double click on the file you just created, select run in terminal and hey presto your done. You could if you want now copy this file to the /usr/local/bin directory to allow everyone who uses the system to access it if you like. If you do that you will probably also want to add a menu entry for it using the System -> preferences -> main menu tool, don't forget to select run in terminal when you create the menu entry.

Works for me and only takes about ten mins from start to finish to set up.

peter

Oh I will attach the deb file to this as well (I hope)

---

