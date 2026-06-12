---
title: "Google Earth won't work on Ubuntu 11.04"
date: 2010-12-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by HorseBox on 2010-12-18
I used to download a .bin file from the Google Earth download page and then I'd just chmod it and run it with the terminal and a GUI installer would come up and install the program fully. Now I can only find a .deb file on the download page and it installs the google-earth-stable package (which is already in the repositories). When I run google-earth now nothing happens though. The only other package in the repositories is googleearth-package. 
[IMG]http://img43.imageshack.us/img43/9099/screenshot1lk.png[/IMG]
The download page provides a .deb but I'm gonna see if this program makes one that works. Why did google earth suddenly become such a pain in the *** to install?

---

### Post by nilarimogard on 2010-12-19
See how to install Google Earth 6 in Ubuntu, here: [http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html](http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html)

---

### Post by howefield on 2010-12-19
Moved to Natty Narwhal Testing and Discussion.

---

### Post by ronacc on 2010-12-19
thanks for the heads up , I just had to install lsb-core to get it to work , I did have to run it the first time from its own directory with ./googleearth after that it runs from the icon .

---

### Post by alphacrucis2 on 2010-12-19
> **ronacc said:**
> thanks for the heads up , I just had to install lsb-core to get it to work , I did have to run it the first time from its own directory with ./googleearth after that it runs from the icon .

At least the 6.0 beta seems to actually work in both Maverick and Natty. I could never get 5.2 to work at all so I had been using 5.1 until the 6.0 beta came out.

---

### Post by SR_ELPIRATA on 2010-12-22
BTW can anyone provide a link for downloading the alpha (11.04) cause the official link doesnt work for me (after 350MB it stops working and I've tried this 3 times in 3 separate days).

---

### Post by dext on 2010-12-22
> **SR_ELPIRATA said:**
> BTW can anyone provide a link for downloading the alpha (11.04) cause the official link doesnt work for me (after 350MB it stops working and I've tried this 3 times in 3 separate days).

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-December/000793.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-December/000793.html) [http://www.ubuntu.com/testing/natty/alpha1](http://www.ubuntu.com/testing/natty/alpha1)

---

### Post by Yumi on 2011-03-25
Any update on the situation? Has anybody Google-Earth working on Natty?

Michael

---

### Post by cariboo on 2011-03-25
Did you try the instructions  in post #2, I just followed them and now  have Googleearth working on my 64-bit Natty install. All you have to do is copy and paste the instructions into a terminal

---

### Post by Yumi on 2011-03-26
That link in #2 does not open as so many here in China. But I will find another site and give it a go. Thanks for confirming that it is working.

Michael

---

### Post by Yumi on 2011-03-26
Found a fairly new help page from Feb. 2011 on [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by beew on 2011-03-26
It works.

Install lsb-core with Synaptic and then down load the .deb file from googleearth.
[http://www.google.com/earth/download/ge/agree.html]("http://www.google.com/earth/download/ge/agree.html") Right click and wait for it to install and that's it (you may want to install gebi and make it the default to install .deb file, otherwise the Software Center will do the installation, it is kind of slow to start up)

---

### Post by Yumi on 2011-03-26
My software center says "Package is of bad quality". Gdebi installs but the result is unusable. Have to change the settings of Google-Earth I presume.

Michael

---

### Post by beew on 2011-03-26
Did you install lsb-core?

---

### Post by Yumi on 2011-03-26
Yes. Without it Google would not start.

Michael

---

### Post by shantiq on 2011-03-26
ok did all this



> [COLOR=#000000][FONT=Times New Roman][COLOR=#555555][FONT=Arial]So let's **install lsb-core:**
sudo apt-get install lsb-core

**1.2)** Install Google Earth package which will automatically create a Google Earth .deb

**32bit:**
sudo apt-get install googleearth-package cd && make-googleearth-package --force
**64bit:**
sudo apt-get install googleearth-package ia32-libs cd && make-googleearth-package --force
**1.3)** The last command above will create a Google Earth .deb file (it's called /googleearth_6.0.0.1735+0.5.7-1_i386.deb on my system) which should be available in your home folder. Install it like you install any other .deb.


Now Google Earth 6 should work.
[/FONT][/COLOR][/FONT][/COLOR]and it shows up in synaptic as googlearth-package but does not start and does not appear in applications

```
googleearth: command not found

```   or google-earth-stable does not start


so a bit confused here:KS

---

### Post by MarcusA on 2011-03-26
[IMG]http://oi54.tinypic.com/24e9l36.jpg[/IMG]

I can open GE, but it looks like this :( pretty unusable lol

Well, I deleted it to try reinstalling later, but the icon is still in my apps list :P Anyone know how to delete the icon? thanks

I also get that "bad quality error" with the .deb -> it works when I right click on the .deb and choose open with GDebi package installer, however it looks like my screenshot again wit supertiny and blurry text...

---

### Post by beew on 2011-03-26
> **Yumi said:**
> My software center says "Package is of bad quality". Gdebi installs but the result is unusable. Have to change the settings of Google-Earth I presume.

Michael

I don't know. My installation took less than a minute and everything works, including the Panoramio pictures that used to show up as blank in earlier versions of ge. 

Maybe your download was corrupted or something, try download the deb again and see what happens.

P.S. If you are using 64 bit you may need some extra libraries (like ia32-libs) though I am not sure since I am on  32 bit.

---

### Post by beew on 2011-03-26
@MarcusA

To delete the launcher go to Main Menu and choose "Internet" on the left panel, the googleearth icon will appear on the right panel, just highlight and delete.

Now how do you go to the main menu depends on whether you are on Unity or the classical desktop.

In Unity click "Applications" on the Unity bar and then when the dash opens on the search box type main menu.

If you use the classic desktop it is under system > preference.

---

### Post by MarcusA on 2011-03-26
> **beew said:**
> @MarcusA
In Unity click "Applications" on the Unity bar and then when the dash opens on the search box type main menu.


Thanx mate :P so simple yet I'm clueless most of the times haha

---

