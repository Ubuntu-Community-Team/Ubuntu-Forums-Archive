---
title: "Howto: Sebrent TV/FM card (saa7130) making it work"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by mrpixels0 on 2008-03-13
Howto for the : Sebrent Analog Tv + FM tuner card (SAA7130 with TDA9887 and without TDA9887).

I wrote this in the hopes that either a new linux user or an experinced one can use it to get this TV/FM card working on thier machine with little to no trouble at all, I have done my best to ensure it is accurate but as with anything in life
you can never be totally sure of anything. so if you use it and it does not work for you just email me at [email]mr.pixels0@gmail.com[/email] or send me a PM or just post it here in this thread and I will do my best to help you get it working.

Read the following completly and make sure you understand it before you use the info contained here (this applies to new new linux users only, intermidate and expert users can ignore this warning).


so here it is:

Follow the Steps Below to get it working:

Open a Terminal window by clicking on Applications->Accessories->Terminal, once the window is open type the following:



Step 1:

sudo nano /etc/modprobe.d/saa1734 and hit enter
next you will be asked for your password enter and press the enter key.

now in the nano editor type in the following lines pressing enter at the end of each one.

alias chr-major-81 videodev
alias chr-major-81-0 saa7134 
options saa7134 card=42 tuner=43 oss=1

now press the control key (ctrl) and the "x" key at the same time, you will be asked if you want to save file: saa1734 say yes by pressing "y" key on the keyboard.



Step 2:

now this step is only needed if you have an Intel HDA onboard sound card of the following families:

82801H (ICH8 Family) HD Audio Controller
82801G (ICH7 Family) High Definition Audio Controller (rev 01)

or anything that even comes close to the above then do this:

type: sudo apt-get install linux-backports-modules-generic and press enter
it will ask you a few questions say yes to all of them by pressing the "y" key on the keyboard.

wait for it to finish.



step 3:

now type: sudo rmmod saa7134_alsa && sudo rmmod saa7134 && modprobe saa1734 and press enter on the keyboard.

reboot your machine and you should be good to go with tvtime and kradio or whatever apps you use for tv and radio viewing/listening.




trouble shooting:

Q: I did this and I get a scrambled picture why ?.

A: most likely your card has a TDA9885/6/7 Module requirement,and you will need to compile it like I did. 

to do this open a terminal and type : sudo apt-get install mercurial linux-headers-$(uname -r)build-essential and press enter.

enter your password when prompted, wait for it to finish.

Now get the v4l-dvb-8dd55a231e6a.tar.gz  using your browser go to [HTTp://linuxtv.org/hg/v4l-dvb](HTTp://linuxtv.org/hg/v4l-dvb)

when the page loads, look at the left side and in small white writting you will see the word "summary" on this same line at then end you will see an orange hyper-link named "gz" click on it and choose save to disk when asked.

now put it in your home directory by going to the tool bar at the top of the screen and click on places->home folder click it once, now you will see a window just drag it from your desktop and drop it here.
now in this window you will right click on this file with your mouse and choose "extract here", now you will see a folder with the same name as the tar.gz file you downloaded now to make easier to change in to that folder from the terminal right click on it with your mouse and choose "rename" and call the folder "v4l" and press enter. 
now close the window for your home folder and open a terminal and type "cd v4l" and press enter
you will now be in the v4l folder now type "make" press enter wait for it to finish.
now type "sudo make install" press enter next you will be asked for your password type it in and press enter now this will take a few minutes to complete when it is done you will see a prompt and a flashing cursor. 
now after this is all done type "modprobe tda9887" press enter, now close the terminal and reboot your computer and you should be good to go.


Q: I get picture on the tv and the radio app shows I have a good signal but I hear nothing !!.

A: got to system->preffrences->sound click on it once and choose alsa for sound events and music and movies and where it says default mixer choose HDA Intel and in the list below select PCM as the defualt mixer track.

now I use tvtime so it sees this automaticly but kradio you need to tell it to use the same thing you set the sound prefs to.

now restart your app(s) and you should now have sound with it as well as picture / signal.

if anyone reading this would like to add to this howto for this card feel free and I will update this how to with the new info to maintain continuity. or if you would like to report an error on my part feel free to do so and I will update with the new info.

---

### Post by nzomosky on 2008-05-09
Thanks alot mrpixelso.....will adapt your solution to my problem later....will holla if it works!

---

### Post by Chet Hagerbaumer on 2008-05-10
I'm having trouble getting TVTime to work.  I followed your instructions to the letter and it worked great (for about 10 mins).  I tried to change the video hue setting in the pop-up window and the program closed.  Since then all I can get is the TVTime Window to open for about two seconds and then it goes away.

What's up with that.     Help!!!!!!!!!!

I would apreciate any suggestions that you can provide.

Thanks,
Chet H.

---

### Post by trevelyan on 2008-05-19
WOW... i did it!! it works now.. i did as described except that i changed the card number to 27 which is my card or so i think as its a much TV but im not sure exactly which one. this is great, most channels work. there is just a few channels that dont get a signal.. i dont know why? any one have any ideas why this would happen???

Thanks mrpixels0!!

---

### Post by trevelyan on 2008-06-02
well... i foudn why that happened.. it was the tuner number. i had to use tuner=2 now all channels work :D

---

### Post by mrpixels0 on 2008-06-11
Sorry Folks about not replying sooner, but I have been ill and I am still recovering from it. I will try to answer every post here that I have missed and once again I am sorry I have been away for so long.

MP0

---

### Post by r3dd3vil on 2008-07-07
Hi! Kind of new with ubuntu but...seem to have a problem. If you can help me I will be kindly thanking you.

That's my tunner card: card=57 -> Avermedia AVerTV GO 007 FM  
I get this after I do what you tell me(without the sound). I hit the number 57 because my tunner is this one. What am I missing here?

ERROR: Module saa7134 does not exist in /proc/modules

Also, after I press dmesg I don't get to see the whole list of v4l2 driver? All packages with that thing are on. What is that v4l2 and how do I do it?
Thank you very much if you can help me!

---

