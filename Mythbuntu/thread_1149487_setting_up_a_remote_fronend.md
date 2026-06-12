---
title: "setting up a remote fronend"
date: 2009-05-05
forum: Mythbuntu
---

### Post by My Name on 2009-05-05
I have had my master frontend/backend running for a few months now and it is working wonderfully.
what i would like to do is set my laptop up as a second fronend so that my sick and pregnant wife can watch movies and tv while she is bed ridden. also it would just be nice to have it set up that way for other reasons.
I have setup the master machine with a standard intrepid desktop and installed mythtv ontop of it.
Could someone hold my hand to help me set my laptop up please?
Or is there a good how to on this.

thanks

---

### Post by klc5555 on 2009-05-05
> **My Name said:**
> I have had my master frontend/backend running for a few months now and it is working wonderfully.
what i would like to do is set my laptop up as a second fronend so that my sick and pregnant wife can watch movies and tv while she is bed ridden. also it would just be nice to have it set up that way for other reasons.
I have setup the master machine with a standard intrepid desktop and installed mythtv ontop of it.
Could someone hold my hand to help me set my laptop up please?
Or is there a good how to on this.

thanks

1) Is your backend properly set up as a Master Backend (not just a standalone?)

2) What OS does/will the laptop run? (Also, is it a fairly zippy laptop, with reliable wireless g or n, or ethernet? And good graphics?)

---

### Post by My Name on 2009-05-05
It is set up as a backend and frontend stanalone at the mo
the lappy is on jaunty
Yeah it's a pretty decent beast, I can watch divx movies over the network without any problems

---

### Post by klc5555 on 2009-05-05
> **My Name said:**
> It is set up as a backend and frontend stanalone at the mo
the lappy is on jaunty
Yeah it's a pretty decent beast, I can watch divx movies over the network without any problems

For the backend. 

In the Mythbuntu control center, in System Services, enable the mysql service (so it can connect over ethernet). In System Role, set to Primary Backend. In the 1st page of the General section of the backend setup, set the two instances of '127.0.0.1' for the location of the database to the actual IP of the backend machine. In the pincode, change from blank to 0000 (so that all other machines can connect).  

In the frontend setup on this same machine, in the "General" section, also indicate the real IP of the backend machine. Make sure the combined Frontend/Backend can still connect to itself before proceeding further. General mythv backend settings instructions can be found here: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend)

For the laptop itself: 

I assume you already have Xine and/or Mplayer installed for watching stuff on DVD. Take Firefox to [http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html) and download the packages for viewing commercial DVDs: libdvdcss2 and w32codecs. Firefox will offer to install them, and it should do so.

Add the mythtv-frontend package and related dependencies (sudo apt-get install myth-frontend). You don't need the backend-only stuff on this machine: no tuners.

From a terminal the command is: mythfrontend

It should stew around for some seconds and complain about not finding a backend, then it should dump you to the config screens. Language first. Then, on the next screen, IP address (NOT 127.0.0.1) of the master backend. User name will remain 'mythtv', database will remain 'mythconverg', the ports will remain the defaults, and the password will be the MySQL password on the backend (available in the /home/mythtv directory in the file 'mysql.txt') 

When the information is entered, mythfrontend will march off to the designated IP to find and connect to the backend. If successful, the frontend starts up in the familiar way, and your job is done. If not, it dumps you back to the configuration screens and you try again.

I've found wireless 802.11b to be good enough for SD digital, 802.11g for SD digital and Analog. The connection needs to remain rock-solid for livetv to avoid ... frustration. (So ethernet is better.) Recordings are more forgiving to wireless bobbles.

Good luck!

---

### Post by My Name on 2009-05-05
Well I was was nearly there on my own I just had the master backend option wrong in mythbuntu control centre.

Now I set it away and had a problem with the video playback. but then I remembered that compiz was on so I switched it off.
Unfortunatly now I seem to have a problem where I can't seem to get the next page to load. I will select watch tv for instance and I can hear the tv but the page stays. it is the same when going into the setup pages in the mythtv frontend.
Any ideas?

I'll have a dig

---

### Post by klc5555 on 2009-05-05
> **My Name said:**
> Well I was was nearly there on my own I just had the master backend option wrong in mythbuntu control centre.

Now I set it away and had a problem with the video playback. but then I remembered that compiz was on so I switched it off.
Unfortunatly now I seem to have a problem where I can't seem to get the next page to load. I will select watch tv for instance and I can hear the tv but the page stays. it is the same when going into the setup pages in the mythtv frontend.
Any ideas?

I'll have a dig

Sorry; can't help here. Never had compiz installed on anything. The laptops I've tended to use for wireless frontends have been old Thinkpads and HP/Compaqs in the 1.2 Gig range --no sense worrying about 3D graphics on machines like that.

Good luck!

---

### Post by My Name on 2009-05-05
A ha!!!! got it
I just ran "mythfrontend.real --reset" and hey presto:P

now just need to work out how to get the videos bit to sync up...

---

