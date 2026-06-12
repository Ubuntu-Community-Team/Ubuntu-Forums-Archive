---
title: "Contribute Today: Firewire Testers Needed!"
date: 2008-03-29
forum: Mythbuntu
---

### Post by majoridiot on 2008-03-29
in an effort to alleviate most, if not all, remaining setup issues with mythbuntu and firewire tuners, the firewire primer for the 8.04 release 
is being completely overhauled.  the first stage of coding on it is completed and ready for testing... specifically by those who have 
Scientific Atlanta set-top boxes, or any other stb that prefers a p2p connection.

testing on this primer is guaranteed quick and painless and does **NOT** require a single change to your mythbuntu configuration-
just follow the simple instructions to compile and test from a command line.

if you are interested and willing to help test this primer, please PM me here or holla @ me in the #mythbuntu irc channel.  please include your
stb vendor and model # in the PM and reply to this thread to keep it bumped toward the top... there are only a FEW days left to get this finished
and tested, so it can make the 8.04 release and the more testers the better!

all help with testing is greatly appreciated and goes to help everyone using mythbuntu and firewire.  responses with source code 
and instructions will start going out around 16:00GMT saturday.

thanks in advance!

**PLEASE SEE POST #3 FOR INSTRUCTIONS AND A BINARY**

---

### Post by c3rb3rus on 2008-03-29
i'm in, just let me know what you need

SA 4250HD

---

### Post by majoridiot on 2008-03-29
the simplest way to do this (i *think*) is for everyone to work with a pre-compiled binary... so one is attached.

as revisions are made, new versions will be posted to ***this*** post, with a notation that it is a newer version.

to test:

1. download the attached *mythprime* and unpack it
```
$ tar xvf mythprime.tar
```

2. open a terminal and change directory to the location of mythprime

3. run it:
```
$ ./mythprime -v
```

**THE( *./* )  before mythprime is critical- otherwise you will run the existing mythprime from /usr/bin**

then, copy and paste the *entire* output into a PM to me here on the forums, with your results.  PLEASE do not paste
directly here, as the output can be long if it is a tough box to prime and we do not need to fill up this thread.

this primer can be tested with either mythtv .20 or .21- if you are running .20 and already have a good firewire setup,
and would like to use this as the default primer, simply back up your existing mythprime and copy this new one to /usr/bin
and:

```
$ sudo cp mythprime /usr/bin/myth_prime
```

if you are running .21, please consult the firewire guide for possible needed changes to your init script before using as your default primer:

[https://help.ubuntu.com/community/MythTV_Firewire#head-17088f2e5e12c855f5b4ebb0b9305ec291db3196](https://help.ubuntu.com/community/MythTV_Firewire#head-17088f2e5e12c855f5b4ebb0b9305ec291db3196)

if you run into difficulties please feel free to PM me.

THANKS FOR HELPING OUT THE PROJECT!

[b][i]current beta version .55b includes power-on of stb, so please test with your stb turned OFF prior to running mythprime.  

multiple firewire cards are also now supported.  You are encouraged to test with more than one firewire card in your system if you have them.

automatic discovery of firewire devices is included- please test with other firewire devices attached too- if you have them- to be sure it is only trying to "prime" stbs.[/b][/i]

---

### Post by volkswagner on 2008-03-29
Glad to contribute.  Running Mythbuntu 7.10 AMD64, Mythtv .21, and SA3250HD.

---

### Post by majoridiot on 2008-03-29
the latest binary has just been posted in #3 above...

the primer should now locate your stb(s) intelligently. :D

run it with:
```
$ mythprime -v
```

and PM me your output, please.

(if you are running non-i386, PM me or email for the latest source.)

THANK YOU!

---

### Post by majoridiot on 2008-03-30
an AMD64 binary has now been posted in #3 as well.  thanks to rhpot1991!

results so far are very encouraging, so please help test!

---

