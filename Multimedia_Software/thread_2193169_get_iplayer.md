---
title: "get_iplayer"
date: 2013-12-11
forum: Multimedia Software
---

### Post by Langstracht on 2013-12-11
Above with apologies to K-Mart.

I cannot get get_iplayer to work.  Well record.

I need to find out whether the problem is a bad installation, poor instructions/documentation, a missing dependency, my O/S, or maybe just me.

So!  It would be VERY helpful if someone could provide a command that "works" (i.e. downloads and saves some programme or other).

I'd like to think that will remove some of the uncertainty about the cause of the problem.

Thanks in advance.

---

### Post by Kirboosy on 2013-12-11
What version of Ubuntu are you running? How did you attempt to install the software?

The [website]("http://linuxcentre.net/getiplayer/installation") claims you can install the package from the software center.

**> [B]Note: If you use Ubuntu 9.10 / Karmic Koala or later you will  find the get-iplayer package in the Universe repository in Synaptic  package manager. **[/B]

Hope that helps!
~Caboose

---

### Post by nothingspecial on 2013-12-11
Are you using get-iplayer from this repository

[https://launchpad.net/~jon-hedgerows/+archive/get-iplayer](https://launchpad.net/~jon-hedgerows/+archive/get-iplayer)

?

---

### Post by dinkypumpkin on 2013-12-12
For future reference, always use the PPA referenced by nothingspecial.  The Ubuntu repositories just pull get_iplayer from Debian, so it will almost always be out of date.  if you're using Ubuntu pre-13.10, it will be broken.  iPlayer is a moving target.  The site referenced by Caboose885 is long dead, but unfortunately still commands a high page rank. For installation, see instead:

[https://github.com/dinkypumpkin/get_iplayer/wiki/ubuntu](https://github.com/dinkypumpkin/get_iplayer/wiki/ubuntu)

---

### Post by Langstracht on 2013-12-12
Sorry - for some reason my e-mail notification seems not to have been working,

In answer to Caboose 885 I had done a: 

```
sudo apt-get install 
```

on both a ubuntu and mint o/s (10.04 and 12 respectively - I know I know they're old).  Neither installation "worked".

I've since installed using the software centre on both machines ... and they don't work either.

In answer to dinkypumpkin - I'm not sure which repository it is coming from.  

I'll happily give it a try to add nothingspecial's repository. 

But how do I ensure that the download comes from there?

And --- does NO ONE have a working get_iplayer record command.  That strikes me as REALLY odd.

---

### Post by dinkypumpkin on 2013-12-12
Plenty of people have a working version of get_iplayer. It's just that you don't - yet.  Follow the instructions I referenced and you will.  The version installed from the PPA will replace the version installed from Ubuntu repositories regardless of whether you installed via apt-get or Software Centre.  You can tell if you're using the PPA version by running:

```
get_iplayer -V
```

to print the version string, which should contain "ppa".

---

### Post by Langstracht on 2013-12-12
Well, I still don't understand this reluctance to share ... but I executed all the commands of [https://github.com/dinkypumpkin/get_iplayer/wiki/ubuntu](https://github.com/dinkypumpkin/get_iplayer/wiki/ubuntu) ... and watched loads of error messages go by.

And at the end of the day when I ran:

```
get_iplayer --get 807
```

I got

> INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: No specified modes (flashhigh,flashstd,flashnormal) available for this programme with version 'default' (try using --modes=)
ERROR: Failed to record 'Prime Minister's Questions - 11/12/2013 (b03lpctl)'

For what it may be worth, when I ran:

```
get_iplayer -V
```


I got:

> get_iplayer v2.79, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Sure hope someone can steer me through this morass ...

---

### Post by nothingspecial on 2013-12-12
Well you still have an old version of get-iplayer

```
$ get-iplayer -V
get_iplayer 2.85-ppa16, Copyright (C) 2008-2010 Phil Lewis


```


> **Langstracht said:**
>  I executed all the commands of [https://github.com/dinkypumpkin/get_iplayer/wiki/ubuntu](https://github.com/dinkypumpkin/get_iplayer/wiki/ubuntu) ... and watched loads of error messages go by.



What errors did you get?

---

### Post by Langstracht on 2013-12-13
Since you have said that I do not have a/the new version .,. might not it be better that you told me how I CAN get a/the new version rather than explore what's wrong with the one I got.

Besides the number of errors far exceeded the lines retrievable from the display AND my ability to recall them.

Thanks in anticipation of your MUCH NEEDED help.

---

### Post by coldraven on 2013-12-13
On Ubuntu 12.04 I have installed get_iplayer from the Software Centre, it's version 2.80-1.
It is working fine for me. Did this command yesterday, the last episode of Pilgrim.
```
get_iplayer --get 10106
```

---

### Post by dinkypumpkin on 2013-12-13
> **coldraven said:**
> On Ubuntu 12.04 I have installed get_iplayer from the Software Centre, it's version 2.80-1.
It is working fine for me. Did this command yesterday, the last episode of Pilgrim.


That version of get_iplayer only half works.  It cannot download TV programmes.

---

### Post by dinkypumpkin on 2013-12-13
> **Langstracht said:**
> Since you have said that I do not have a/the new version .,. might not it be better that you told me how I CAN get a/the new version rather than explore what's wrong with the one I got.

Besides the number of errors far exceeded the lines retrievable from the display AND my ability to recall them.

Thanks in anticipation of your MUCH NEEDED help.

You have received the one and only set of instructions to install a fully-working packaged build of the latest version of get_iplayer for Ubuntu.  Don't assert otherwise, and don't accuse the people providing exactly the information you need of a "reluctance to share".  If the instructions you were given didn't work, then no Ubuntu users would be able to install the latest get_iplayer, and that is patently not the case.  If those instructions don't work on your machine, then something is wrong on your machine.  If you won't post your errors, then nobody can help you figure out what that is.  If the errors are really so voluminous, then run the first command in the instructions, post the errors, get feedback, make corrections and re-run, then move on to the second command, and so on.  Alternatively, install get_iplayer manually:

[https://github.com/dinkypumpkin/get_iplayer/wiki/manual](https://github.com/dinkypumpkin/get_iplayer/wiki/manual)

---

### Post by Langstracht on 2013-12-13
Thanks for your response.

As I think I said, I've stayed with ubuntu 10.04.  Why? Because I have been told that there is a VERY good chance that 12 and 13 will not work on my machine because of video card incompatibilty.  And I'd just as well not take the chance.

That said the version of get_iplayer it gave me was/is 2.85.

Amazingly I just tried your working command ... and it also worked for me.  But it IS for audio ... so perhaps my problem is (just) with video which is what I have been trying to download.

Would you/anyone have a working command for video that I can try.

On the other machine, as I think I also said, I am using Mint 12 (for basically the same reasons as before).  The version it offered up was/is 2.79.  And, less amazingly this time, your command worked there too.

Thereby re-doubling my request for a working video command.

Can you/anyone help?

TIA

---

### Post by Langstracht on 2013-12-13
Sorry - I hadn't realized that dinkypumpkin had replied to coldraven before I did.  

So I guess I am getting what I should be getting so to speak.

So, if I may, may I ask another question.

Should the latest get_iplayer work on ubuntu 10.04 and Mint 12 or not?

If it should then I shall try this one more time.  And, of course, if it won't then there's not much point.

Again, TIA.

---

### Post by dinkypumpkin on 2013-12-13
> **Langstracht said:**
> 
So I guess I am getting what I should be getting so to speak.

So, if I may, may I ask another question.

Should the latest get_iplayer work on ubuntu 10.04 and Mint 12 or not?


So it appears you can install from the PPA after all.  get_iplayer works fine on Ubuntu 10.04.  I don't know about Mint 12.  If you can't download video, then post the full command line, the programme episode you were trying to download, and the output from get_iplayer.

---

### Post by Langstracht on 2013-12-13
I tried it with the following results:

```
get_iplayer --get 1250
```

> Matches:
1250:	World News Today - 12/12/2013, BBC News, News,TV, default

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: No specified modes (flashhigh,flashstd,flashnormal) available for this programme with version 'default' (try using --modes=)
ERROR: Failed to record 'World News Today - 12/12/2013 (b03l7g1h)'


This was the (kind of) message I was getting before ... prompting me to try various and sundry "mode" additions to the command line (like --mode flashhigh and --vmode= flashnormal and --modes =flashstd) all to no avail.

And thereby prompting my request for a working command ...

---

### Post by dinkypumpkin on 2013-12-13
> 
[COLOR=#000000][I]INFO: No specified modes (flashhigh,flashstd,flashnormal) available for this programme with version 'default' (try using --modes=)
[/I][/COLOR]
[COLOR=#000000]
That typically means you are using get_iplayer outside the UK.  You must have a UK IP address to access iPlayer TV programmes.[/COLOR]

---

### Post by Y^2om&amp;#7sgP on 2013-12-13
did you add the ppa that was suggested ?

sudo apt-add-repository ppa:jon-hedgerows/get-iplayer

sudo apt-get update

sudo apt-get install get-iplayer

(although sudo apt-get upgrade will also probably work)

---

### Post by Langstracht on 2013-12-13
<expletive deleted> I should have realized that!  But I did not.  And suspected everything except geography (no I am not in the U.K.) for the problem.

Sorry for taking up of time and bandwidth.  An edifying experience none-the-less.  For hopefully more than just me.

I'll mark this as solved - albeit in an unhappy way.

Tx

---

