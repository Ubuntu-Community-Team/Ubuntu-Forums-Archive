---
title: "HOWTO:  Unrecognized/Incorrectly Recognized saa7134 TV Tuner Cards"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-04-13
Most of the information in this post is contained in the [_Gentoo saa7134 wiki_]("http://gentoo-wiki.com/HARDWARE_saa7134"), but as people still are having a lot of problems with these cards, I thought I would try to summarize what seems to have worked.

Most generic TV tuner cards seem to be based on the Phillips saa7134 chipset.  These cards often have a problem being automatically detected by Ubuntu on bootup.  If you can't get you're card to work, it could be a problem like this.

Because there are so many different saa7134 cards, when the driver is loaded, your system needs to know which type of card you have.  Sometimes this can be determined automatically, but often it can't, so you have to figure out what card number(s) work for you.  There is a list of many cards and their numbers on the Gentoo page linked above, and you may also be able to see the list by running the command:
$ dmesg

If you can find your card number in the list, try loading the saa7134 driver with that card number.  To do this, first remove the module (and the sound module that depends on it):
$ sudo rmmod saa7134_alsa
$ sudo rmmod saa7134

Then load the driver with the card number:
$ sudo modprobe saa7134 card=<card number>

Then try running TVTime and see if you can tune channels.  If it worked, then to have the module load with the correct card number every time you start up your machine, edit the file /etc/modprobe.d/options by adding the line:
Options saa7134 card=<card number>

If, however, you still can't tune channels with the card number that was supposed to work (as was the case for me), you can try different card numbers.  In my experience, I found that I could tune channels with about a third of the card numbers, but I only got sound with a few.  This script will do this automatically:

```
#/bin/sh
MAXTUNER=69
i=0

while [ $i -lt $MAXTUNER ];
do
  rmmod saa7134_alsa saa7134
  modprobe saa7134 card=$i
  echo "Actual card is:" $i
  sleep 1 # this is to make sure /dev/video is registered when tvtime starts
  tvtime
  i=$(($i+1))
done
```

Just create a new file, called perhaps script1.  Paste the text above into the file and save it.  Then, change the permissions to make it executable, and execute it:
$ sudo chmod 755 script1
$ sudo ./script1

What the script does is load the saa7134 module with a card number, then run TVTime so you can see if it works.  When TVTime opens, make sure that you are using the tuner input, then try to change channels.  If it works, go to the command prompt and type CTRL+C to stop the script, and then edit /etc/modprobe.d/options as I mentioned above with the card number that worked.  If it didn't work, then simply close TVTime, and the script will load the driver with the next card number and open TVTime again, and so on.  There are 69 card numbers, but as I mentioned above, about a third of them worked for me for video, so if you get to card number 20 or 30, and you haven't gotten any TV signal, there is a good chance that this will not fix your problem.  If that is the case, I recommend you check your connections - i.e. plug the cable that you have going to your TV card straight into a television to verify that you actually have a signal.

Also, I have found that occasionally, the system can become unresponsive during this process.  If this happens, it is best to just reboot.  Then, before you start the script make sure you change the line:
```
i=0
```
to:
```
i=<card number>
```
Where, obviously, <card number> is the one after the one that made your system become unresponsive.

---

### Post by the_mouse on 2007-04-29
I'm using your script to determine the proper card number, but everytime when it tries to unload the saa7134 module, it gets 
ERROR: Module saa7134_alsa is in use
ERROR: Module saa7134 is in use by saa7134_alsa
and goes on, so I don't think it has any effect at all :(
I tried to load card=3 and 2 for Chronos Video Shuttle 2 tv card, but when I start tvtime-scanner (I don't have a standart frequency table) there's 'no signal' when running through the frequences :(

---

### Post by josesanders on 2007-04-30
The saa7134_alsa module has to do with sound for your TV card.  Is there some process running that could be using this module?

---

### Post by ivolinux on 2008-06-10
my card is a saa3174, I can see but not hear any sound, 

kgio@secondo:~$ sudo modprobe saa7134_alsa
FATAL: Error inserting saa7134_alsa (/lib/modules/2.6.24-18-generic/ubuntu/media/saa7134/saa7134-alsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)



I don't know how resolve this problem please help

---

