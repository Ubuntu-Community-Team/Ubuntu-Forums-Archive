---
title: "Installing Banshee 1.5.2"
date: 2009-11-24
forum: Multimedia Software
---

### Post by avongil on 2009-11-24
Hey everyone,
 
I have a motorola droid and want to check out some of the latest syncing improvements added to the banshee project a few days ago.  I am having a really hard time installing Banshee 1.5.2. I have tried three methods,

1 - with the unstable ppa ([https://launchpad.net/~banshee-team/+archive/banshee-unstable]("https://launchpad.net/%7Ebanshee-team/+archive/banshee-unstable"))
2 - by the 1.5.2 official source
3 - by a git snapshot.

the ppa, should be drop dead simple, but I get nothing at all.  Im still at my current version.

when trying to compile from source I get a could not find ipod-sharp 0.8.5 or later. I scoured the Internet but could only find .8.3.

Can anyone help me install banshee 1.5.2? I'd much rather get the PPA to work.



[URL="https://launchpad.net/ubuntu/+archive/primary/+files/ipod-sharp_0.8.3-1.diff.gz"]
[/URL]

---

### Post by Turtle.net on 2009-11-25
1.5.2 is not in the PPA yet ... :(
We will have to wait a little bit more I guess,

For the install from source I have no idea. Will try it to see if i can find something.

You can find ipod-sharp 0.8.5 [here]("http://fr2.rpmfind.net/linux/RPM/mandriva/devel/2010.1/i586/media/main/release/ipod-sharp-0.8.5-1mdv2010.1.noarch.html") and I guess you could also compile the latest version yourself from svn

it's far too complex for me to try this.
I'll wait :)

---

### Post by avongil on 2009-11-25
I'l compile it myself, I just cannot find it anywhere.  Can someone give me a clue?

I'm a little upset at the Banshee page. It clearly states 1.5.2 is out an to install via the PPA.  Not true. 

I don't want to be a downer, but this is exactly what the linux community does not need. I'd be happy to help with the project and try to help test and debug the software, but it's downright impossible to install, the support is not there (posted on the banshee mailing list via nabble), and the web site is completely inaccurate.   

I think i'm down to one last dependency, ipod-sharp 0.8.5 and have no idea where to even get it. if someone can give me a clue, that  would be great.

Thanks.

---

### Post by HuckleSmothered on 2009-11-26
Been looking for the same thing.
Here's a location that DID work for me:
[https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily)

Basically, add ppa:banshee-team/banshee-daily to the sources list.
The previous ppa:banshee-team/banshee-team doesn't have the latest.

I'm at Banshee 1.5.3 now ... aka 1.6 Beta 4.
... still crashes every time I click on a playlist though ...
A recent development that I thought the upgrade would rectify.

---

### Post by avongil on 2009-11-26
Thanks so much.  That was sooooo easy. 

Works with Motorola Droid.  No crashing on my end when clicking on play lists.

Thank you.

Something very easy turned into lots of frustration.  I hope the Banshee web site is updated to include good information for installing this. I cannot imagine how you figured that out.  I don't want to complain, but this is a good example of why people have a bad attitude towards open source software, even if its high quality like Banshee is.

---

### Post by HuckleSmothered on 2009-12-03
For as long as I've been using Banshee, their website has been out of date in some respect. I found this by getting lucky in Google. Persistance. Mainly due to having another problem that I thought this would fix and repeatedly searching, searching, searching ...

I was asked for specifics on how to do this in a PM but thought I'd respond here for the benefit of others as well. So without further ado ...

Go to **System | Administration | Software Sources**
Go to the tab **Other Software**
Click on **Add**
APT line: **ppa:banshee-team/banshee-daily**
Press **Add Source**
Then close the window.
At this point I usually open a Terminal window and type:
```
sudo apt-get update
sudo apt-get upgrade
```
You can also throw in one of these if banshee's not upgraded automagically:
```
sudo apt-get install banshee
```
Then to check the version:
```
banshee --version
```
Shazam

---

### Post by avongil on 2009-12-03
Two thumbs up. Works great. 

I think Bansee is awesome, but the total lack of web documentation made me look at Songbird. I think its very promising. Check it out!  
Better in every way but has more overhead. I use banshee on my less powerful machines, but I am a songbird convert now.

Easy to install, just download and double click.
[http://skyzim.com/downloads/](http://skyzim.com/downloads/)

---

