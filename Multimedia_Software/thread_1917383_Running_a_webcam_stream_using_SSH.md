---
title: "Running a webcam stream using SSH"
date: 2012-01-29
forum: Multimedia Software
---

### Post by Viking007 on 2012-01-29
Hello fellow Ubuntu users,

Is it possible for me to view my webcam stream from one laptop (running Mac OS Snow Leopard) to my second laptop (running Ubuntu 10.04)? over the internet not LAN? (trying it as a self-learning project)

I know VLC allows that but how would I go about doing it using the terminal?....

Background Info: I am a little bit aware that I could use SSH -X to connect to a computer (in this case my Mac laptop)...I have already established this connection but every time I run:

# open VLC.app 
the VLC opens on my mac instead of my ubuntu laptop; so given that I can't even open vlc on my screen it seems impossible for me to even turn on the webcam!...

Any Help would be appreciated and please I am self-learning so a step by step tutorial would be even better!

Cheers :o

---

### Post by inobe on 2012-01-29
zoneminder

[http://www.zoneminder.com/wiki/index.php/Ubuntu](http://www.zoneminder.com/wiki/index.php/Ubuntu)

---

### Post by Viking007 on 2012-01-29
Thanks inobe, but I was not really looking for an app to do that but rather learn more about SSH and its applications...Should have mentioned before - D'oh!

---

### Post by inobe on 2012-01-30
ssh is a remote beast and requires significant skill to maintain security.

when you start tinkering with things such as that, it takes more than forum advice, in fact, lots of literature, man pages to be exact:P

[http://www.openssh.org/manual.html](http://www.openssh.org/manual.html)

don't get in over your head.

---

### Post by Viking007 on 2012-01-30
> **inobe said:**
> ssh is a remote beast and requires significant skill to maintain security.

when you start tinkering with things such as that, it takes more than forum advice, in fact, lots of literature, man pages to be exact:P

[http://www.openssh.org/manual.html](http://www.openssh.org/manual.html)

don't get in over your head.

I agree it is a beast....I am reading through the literature and not jumping any steps just because I learned about a new command called ssh!...

Honestly, IMHO it is never a bad idea to ask and see if others have already tried and are willing to help!

But thanks for your opinion=;

---

### Post by aeiah on 2012-01-31
issue the ssh command with verbose logging and see what the issue is. as far as i know, os x doesn't run applications using an X server (although you can install X), so that's probably where the problem lies. 

your best bet is probably to broadcast your vlc stream to the LAN the mac is on, and tunnel into your LAN using ssh

---

### Post by Viking007 on 2012-01-31
> **aeiah said:**
> issue the ssh command with verbose logging and see what the issue is. as far as i know, os x doesn't run applications using an X server (although you can install X), so that's probably where the problem lies. 

your best bet is probably to broadcast your vlc stream to the LAN the mac is on, and tunnel into your LAN using ssh

You are absolutely spot on!....I have X installed on the mac and tried the ssh command with verbose and everything seems fine, but I guess Mac OS is what Ubuntu is not (very closed :P)...lol


As for your tip on broadcasting on lan, can you explain me how that could be accomplished or point to some tutorial page?...So far what I've done is: 

broadcast on localhost:8080
then port forwarded that using SSH to my port 8080 (Using ssh -R command)
but when I try to open localhost:8080 on firefox on my own ubuntu, all I get is "Can not open Server"

and Thanks for this idea...not sure why I didn't thought of that before...lol

---

