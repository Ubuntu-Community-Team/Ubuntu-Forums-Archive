---
title: "Dell Inspiron 910 with Ubuntu"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by addyyy on 2009-01-15
I purchased a Dell mini inspiron for Christmas for my daughter.  I was able to get the direct ethernet connection to work fine.  I since purchased a Zyxel router so everything i have can be on line at once (ps3,desktop and the mini).  However the wireless card is either not turned on or it isnt configured properly as i can get ABSOLUTLY NO WHERE WITH THE TERMINAL COOMMANDS ETC ALL I GET IS THAT THERE SEEMS TO BE ONE AND NEXT TO IT IT SAYS IEEE 802.11i  can anyone please help with getting this to work this is extremly frustrating that i cannot speak to someone on the phone.  What a present the thign doesnt even work.  I need help asap.

---

### Post by Sinsinnati on 2009-01-15
What version of Ubuntu are you using? If your daughter doesn't mind you formatting and starting from scratch, check out this site: [http://www.ubuntumini.com/2008/10/user-guides-for-ubuntu-810-intrpid-ibex.html]("http://www.ubuntumini.com/2008/10/user-guides-for-ubuntu-810-intrpid-ibex.html") If, after a completely fresh setup, you still have trouble, it may just be faulty hardware and covered.

In case the empathy applies, I'm not a big fan of sifting through beginner banter either. But this blog is specific to the model and it's nice that someone is cataloguing the trial-and-error tweaking for it.

---

### Post by addyyy on 2009-01-15
It is 8.04

---

### Post by superprash2003 on 2009-01-15
go to the terminal and type lshw -C network .. and post output.. try enabling wifi driver ( if present) under system->admin->hardware driver

---

### Post by addyyy on 2009-01-15
It says command not found

---

### Post by Sinsinnati on 2009-01-15
So you installed the desktop version of 8.04 or you're using the preloaded version (8.04.1)?

---

### Post by addyyy on 2009-01-15
In hardware drivers there is only one device listed and it is enabled and is called wl

---

### Post by addyyy on 2009-01-15
the system says that ndiswrapper is installed when i type in iwconfig in terminal it says 

lo    no wireless extensions

eth1   IEEE 882.11 Nickname **
       access Point:  Not Associated

---

### Post by addyyy on 2009-01-15
It was preinstalled

---

### Post by addyyy on 2009-01-15
in terminal i ran dmesg ! grep -e ndis -e wlan

i got back

[16.442882] ndiswrapperversion 1.52 loaded (smp=yes, preempt=no)
[16.448220] usbcore: registered new interface driver ndiswrapper

thats all it says

---

### Post by addyyy on 2009-01-15
Anyone please?????[]

---

### Post by superprash2003 on 2009-01-16
the command is **lshw -C network**

---

### Post by addyyy on 2009-01-16
It says invalid command    lshw -c network i tried ishw etc all invalid commands

---

### Post by superprash2003 on 2009-01-18
it has to work.. its a capital C .. it is lshw -C network not lshw -c network... note the difference -c and -C

---

### Post by Ted Pitts on 2009-01-18
I'm sorry to butt in but I also bought the mini 9 for christmas and the touchpad does not work at all and I can't log on to the WIFI  (wireless internet at starbucks). When firefox is loaded it says error in downloading... any help here?  Thanks Ted

---

### Post by superprash2003 on 2009-01-19
@ted
  post output of the following commands from the terminal
1)lshw -C network
2)iwconfig
3)iwlist scanning

---

### Post by Ted Pitts on 2009-02-01
for item 1) I got: command not found
for item 2) I got: lo no wireless extensions
                  eth0 "     "         "
                  eth1  IEEE 802.11 NICKNAME: " "
                  ACCESS POINT: Not-Associated                  for item 3) I got: lo interface doesn't support scanning.

Now for the good news: I took my mini to a computer repair shop and they checked it out and got it working for the wireless
(WIFI). They said it was turned off in Networking. So, the only thing that don't work now is the touchpad but I prefer to use a USB mouse anyway.  Thanks much for your help !!!  Ted

---

### Post by Sinsinnati on 2009-02-02
Last I checked, Starbucks' wireless is through T-Mobile. If it's still the case, you'd require an air card and account through them.

---

