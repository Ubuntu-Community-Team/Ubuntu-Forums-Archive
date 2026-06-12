---
title: "Antec Fusion Black V2 lcd"
date: 2008-02-28
forum: Mythbuntu
---

### Post by 4dognight on 2008-02-28
Ok, Im going nuts trying to get My LCD and Volume knob and IR remote to work on this case. 

I have read all the posts out there and had asolutely zero success in getting any of the 3 to work.

I have the LCD not the VFD display. It does have the IR receiver and the volume knob.

Most of the posts i read have me compiling from scratch, LCDd, lircd. Does this mean I disable the remote in the Myth control center? 

If I understand correct...

By enabling LCD device in Myth, this cause mythlcdserver to communicate with LCDproc to display the LCD screen.

What is used to control the volume knpb?

Do I enable the remote in the myth config and which one do  I select. I have a MCE compatible remote from my Gyration keyboard/remote combo.

Can someone help me cure my headache? I will submit whatever output you ask for.

---

### Post by axelsvag on 2008-02-29
Which tutorials have you used?

---

### Post by 4dognight on 2008-02-29
I finally got the LCD to work using a combination of these two sites.
[http://codeka.com/forums/viewtopic.php?f=3&t=22&st=0&sk=t&sd=a](http://codeka.com/forums/viewtopic.php?f=3&t=22&st=0&sk=t&sd=a)

That site got me the latest version of lirc_imon. But I found that it wasnt installing in the correct directory, as pointed out by this web site.

[http://hubpages.com/hub/How-to-configure-an-Antec-Fusion-Black-display-on-Linux](http://hubpages.com/hub/How-to-configure-an-Antec-Fusion-Black-display-on-Linux)

Once I copied the new lirc_imon in the correc tdirectory it worked.


Now I m trying to get the volume knob to work, using this site, but I am unsuccesful.

[http://www.mythtv.org/wiki/index.php/Volume_Knob_on_Antec_Fusion](http://www.mythtv.org/wiki/index.php/Volume_Knob_on_Antec_Fusion)

Also, I have no idea how to get my MCE compatible remote to work.

---

### Post by myth-karl on 2008-03-09
I recently built a Mythbuntu box using an Antec Black Fusion v2.

I followed the instructions on the codeka website with no hitches except this line.

~/lcdproc-0.5.2$ aclocal && automake && autoconf

I had to run
~/sudo aclocal && sudo automake && sudo autoconf otherwise i got permission denied errors. 

But what i did get was something about flags required or something but it did not look like an error.

After editing my conf file to point to the right driver and dropping the contrast to 200 also, I now have a clock displayed. 

If I run ~/LCDd I get "LCDproc server" and some other stuff displayed but that is all i have managed to get it to do. I have enabled LCD in Myth but nothing happens.

Any Ideas?

---

### Post by 4dognight on 2008-03-09
Check you rmyth logs for any errors. probably permission errors, is my guess.

I never did get the volume knob to work. And I dont really need the IR receiver , so I gave up on that too. I have a gyration remote, which uses RF for the PC remote.

---

### Post by wombo on 2008-03-10
I also am having some trouble with this line, with or without the Sudo command
```
aclocal && automake && autoconf
```

This is the output
```

htpc@mythtv:~/lcdproc-0.5.2$ aclocal && autoconf && automake
The program 'aclocal' can be found in the following packages:
 * automake
 * automake1.4
 * automake1.7
 * automake1.9
 * automake1.8
Try: sudo apt-get install <selected package>
-bash: aclocal: command not found
htpc@mythtv:~/lcdproc-0.5.2$

```

does anyone have any ideas?

---

### Post by 4dognight on 2008-03-10
Looks like your missing automake.

You need to install it.

sudo apt-get install automake

---

### Post by cjs500 on 2008-03-27
Hey 4dog, I wasn't able to get my LCD working yet. I hope your links work. I've tried so many howtos and haven't gotten a single pixel out of my LCD yet. I know it works since I tried in Windows just to make sure.

BTW, I did get my IR and Volume control knob to work. I've posted this on the forum. Here's the link incase you are still struggling with it. 

[http://ubuntuforums.org/showthread.php?t=723003](http://ubuntuforums.org/showthread.php?t=723003)

The Volume control knob... asuming you have a USB connector attached to your motherboard from the fusion case... can be setup in the lircd.conf file along with the remote control buttons.

I'm using mythbuntu 7.10 at the moment. I didn't need to install any patched version of the lirc source. I've detailed as much as I can think of in the post.

Enjoy the novel! :P

---

### Post by 4dognight on 2008-03-27
I will have to check it out. I upgraded to .21, so now Im still trying to get through all the new features and bugs it introduced.

---

