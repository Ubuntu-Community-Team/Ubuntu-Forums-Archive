---
title: "Any way to view these BBC videos??"
date: 2013-03-01
forum: Multimedia Software
---

### Post by sdowney717 on 2013-03-01
[http://www.bbcattic.org/blueprint/media/belfast_elk.shtml](http://www.bbcattic.org/blueprint/media/belfast_elk.shtml)

Just came across them and they cant play at all. Then if you try the ram files it claims it is a text file. SO why is it doing this?
Looking at it in chrome.

---

### Post by Rebelli0us on 2013-03-01
It's not playing here either. Could be bad page design.

---

### Post by sanderj on 2013-03-01
> **sdowney717 said:**
> [http://www.bbcattic.org/blueprint/media/belfast_elk.shtml](http://www.bbcattic.org/blueprint/media/belfast_elk.shtml)

Just came across them and they cant play at all. Then if you try the ram files it claims it is a text file. SO why is it doing this?
Looking at it in chrome.

Are you in the UK?

I am NOT, and I can't even connect to the server

telnet rm-acl.bbc.co.uk 8080
Trying 212.58.251.74...
telnet: Unable to connect to remote host: Connection refused

AFAIK, that's on purpose as the BBC doesn't want users 'abroad' to watch BBC content

---

### Post by shantiq on 2013-03-01
only UK for vids altho radio progs work all over the work i think


opened with opera and firefox fine both times

does not open in mplayer for me [text file]   but perfect in vlc 2.05 standard for 12.04

 my guess is mplayer can do it too with correct plugin/settings    but try vlc should be fine   on chrome right click and save ram file [where it says view as real media]then open with vlc


hope that works

---

### Post by sdowney717 on 2013-03-01
I am in the USA, so that makes sense.
I tried using VLC to open the ram link and it had errors connecting.
I have seen some BBC content posted to youtube.

---

### Post by sanderj on 2013-03-01
> **sdowney717 said:**
> I am in the USA, so that makes sense.
I tried using VLC to open the ram link and it had errors connecting.
I have seen some BBC content posted to youtube.

There is a solution: get a cheap VPS with Ubuntu in the UK itself, and then use that VPS as a SSH-SOCKS tunnel. See [http://ipv6-or-no-ipv6.blogspot.nl/2011/11/fun-with-socks-ipv6-and-ssh.html](http://ipv6-or-no-ipv6.blogspot.nl/2011/11/fun-with-socks-ipv6-and-ssh.html)

---

### Post by haqking on 2013-03-01
> **sanderj said:**
> There is a solution: get a cheap VPS with Ubuntu in the UK itself, and then use that VPS as a SSH-SOCKS tunnel. See [http://ipv6-or-no-ipv6.blogspot.nl/2011/11/fun-with-socks-ipv6-and-ssh.html](http://ipv6-or-no-ipv6.blogspot.nl/2011/11/fun-with-socks-ipv6-and-ssh.html)

or even cheaper, actually FREE.  use TOR. and change your exit node's fingerprint to UK and to any other country you want to appear coming from.

No need to purchase a VPS then.

---

### Post by andrew.46 on 2013-03-01
> **sanderj said:**
> There is a solution: get a cheap VPS with Ubuntu in the UK itself, and then use that VPS as a SSH-SOCKS tunnel. See [http://ipv6-or-no-ipv6.blogspot.nl/2011/11/fun-with-socks-ipv6-and-ssh.html](http://ipv6-or-no-ipv6.blogspot.nl/2011/11/fun-with-socks-ipv6-and-ssh.html)

A better solution would be for content providers to stop trying to control their audience in this way :)

---

### Post by haqking on 2013-03-01
> **andrew.46 said:**
> A better solution would be for content providers to stop trying to control their audience in this way :)

Indeed, 1984 is here

---

