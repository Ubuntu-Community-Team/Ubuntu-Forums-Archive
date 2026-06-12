---
title: "Frontend Starts Before Network Connection Established"
date: 2010-09-18
forum: Mythbuntu
---

### Post by Erlander on 2010-09-18
I am trying to setup a pc next to our tv and want an automatic start to Myth.  This is to connect back to a remote backend via a wired gigabyte lan.

When I set this up the frontend starts before the network connection is established so that I get thrown out to the setup and no upnp screen.

If I just hit enter each time till I get through the General Setup by the time I have done that the connection is made and all works.

Or if I disable the auto startup of Myth and go to the Ubuntu screen and start Myth after the network connection it also all works.

So, is there any way I can delay the Myth startup until after the network connection is made?

---

### Post by ian dobson on 2010-09-18
Hi,

The frontend is started by the script mythtv-frontend which starts mythvfrontend.real. So all you need to do is add a sleep X seconds just before frontend.real is called.

Another way would be to add a loop that checks the output of ifconfig and waits until your ethernet interface has a ip address.

Hope this helps

Regards
Ian Dobson

---

### Post by Erlander on 2010-09-18
Thank you Ian.

Given my poor programming skills I think I'll go for the sleep x seconds option.

In Lucid it seems the relevant script is /usr/bin/mythfrontend  (no hyphen).

Would :

"sleep 5 seconds" be the correct syntax?

Thank you.

Rob

---

### Post by ian dobson on 2010-09-18
Hi,

Jusr edit /usr/bin/mythfrontend and add a line
sleep 5

somewhere at the top of the file, just after the header/comments something like:-
#!/bin/sh
# Mario Limonciello, March 2007
# partially merged with startmythtv.sh by Michael Haas, October 2007
sleep 5

Maybe you'll need more/less than 5.

If I get afew minutes I'll have a look at writing a "wait for ip address before continueing" script.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-09-18
Hi,

OK, it didn't take long to bang something together:-

```

Res=""
while [ "$Res" = "" ]; do
  sleep 1
  Res=`ifconfig | grep inet | grep -v "127.0.0.1"`
done

```

What the script does is:- sit in a while/do loop, running ifconfig once a second and looking for an ip address that isn't local host (127.0.0.1).

I can't test this at the moment but I imagine it should work.


Regards
Ian Dobson

---

### Post by Erlander on 2010-09-18
Many thanks for that Ian.

I started with sleep 5 but had to lift it to 10 where it seems ok.

I'll give your ip address script a try tomorrow as its getting late here and I don't want to think scripts all night so will give it a break for now.

Thank you for your help.

will report back.

Rob

---

### Post by Erlander on 2010-09-19
```
Res=""
while [ "$Res" = "" ]; do
  sleep 1
  Res=`ifconfig | grep inet | grep -v "127.0.0.1"`
done
```
This did not work for me and I have reverted back to 
```
sleep 10
```
However I will try again at another time.  The situation is complicated by only having an analogue crt tv as a monitor and appalling text quality.  I had to do it directly on that pc and the tv as I wanted to use gedit and copy and paste your code.  With the image quality available this was difficult.  However to put it back to sleep 10 I used ssh from another pc and nano. Gedit doesn't seem to work from another pc on the network.

I will have another try later on when my wife is no longer watching tv.

Thank you.

---

### Post by ian dobson on 2010-09-19
Hi,

OK, I'll see what I can do to test the code. The problem is that I can't easly test it as I only have access to me linux boxes through a network connection.


I have a "spare" box that I can miss use, but at the moment it's missing a graphic card/monitor, so it might take a day or so to get the bits from my son.

Regards
Ian Dobson

---

### Post by Erlander on 2010-09-19
I'll probably be able to have another try tomorrow so don't worry too much.

In the meantime the sleep 10 is working.  In addition I'm still working this frontend up and its not really fully operational yet.

Thank you.

Rob

---

### Post by klc5555 on 2010-09-19
I thought this problem was sort of addressed way back in 9.04. The problem being that initialization of the network was moved in 8.10 to the graphical shell with the abysmally slow NetworkManager, rather than taking place earlier in the bootup where it formerly did.

The primary solution revolved around disabling NetworkManager and initializing the network earlier in the boot sequence by modifying /etc/network/interfaces  The relevant thread was here: [http://ubuntuforums.org/showthread.php?t=1159824&highlight=network+manager+slow](http://ubuntuforums.org/showthread.php?t=1159824&highlight=network+manager+slow)

No reason thechump's and djieno's solution shouldn't still be valid.

---

### Post by Erlander on 2010-09-20
Hi Ian.

I've set up Remote Desktop which I've never used before.

I used it to modify /usr/bin/mythfrontend with your script.

It doesn't seem to work as I get the no upnp screen asking for the language I want.

went back and put in sleep 10 and that is working.

Thank you.

Rob

---

### Post by ian dobson on 2010-09-20
> **Erlander said:**
> Hi Ian.

I've set up Remote Desktop which I've never used before.

I used it to modify /usr/bin/mythfrontend with your script.

It doesn't seem to work as I get the no upnp screen asking for the language I want.

went back and put in sleep 10 and that is working.

Thank you.

Rob

Hi Rob,

When I get a chance I'll have a look at it, maybe this evening.

Regards
Ian Dobson

---

