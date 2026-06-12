---
title: "Send text to another IP"
date: 2012-02-13
forum: Networking &amp; Wireless
---

### Post by stlu on 2012-02-13
Help!  This should be bloody simple, but I can't get the answer I need from google.

I have a computer in another location.  The IP is dynamic, and when it changes, its really frustrating because I can't do anything about it until the next time I arrive.

ALL I wanted to do was transmit the IP address of the remote computer directly to my computer.  I have a command that extracts the text off a website so the remote computer is setup to get its own public IP daily.  I am fully comfortable with port forwarding as necessary, I just need to get that information across the internet to my computer.  I am using a host redirect on my end.

First, I thought it was possible to fire off an email from the remote machine, but it looks like this cannot be done unless I acquire an email account/password.

Then I tried **talkd**, but it just plain wouldn't work, plus it looks too interactive and not scriptable.

I have read about a (Windows) command called "net send", which was not exactly what I want, but nothing else came closer to describing the task I want to perform.

Somebody please let me know a simple way, or god help me, I'll open my pc as an NFS server to internet as its looking like the only simple answer :(

---

### Post by haqking on 2012-02-13
> **stlu said:**
> Help!  This should be bloody simple, but I can't get the answer I need from google.

I have a computer in another location.  The IP is dynamic, and when it changes, its really frustrating because I can't do anything about it until the next time I arrive.

ALL I wanted to do was transmit the IP address of the remote computer directly to my computer.  I have a command that extracts the text off a website so the remote computer is setup to get its own public IP daily.  I am fully comfortable with port forwarding as necessary, I just need to get that information across the internet to my computer.  I am using a host redirect on my end.

First, I thought it was possible to fire off an email from the remote machine, but it looks like this cannot be done unless I acquire an email account/password.

Then I tried **talkd**, but it just plain wouldn't work, plus it looks too interactive and not scriptable.

I have read about a (Windows) command called "net send", which was not exactly what I want, but nothing else came closer to describing the task I want to perform.

Somebody please let me know a simple way, or god help me, I'll open my pc as an NFS server to internet as its looking like the only simple answer :(

when you say a machine in a remote locale with dynamic IP do you mean a public facing machine with a dynamic IP such as a Server or a machine behind a router whose IP is dynamic ?

If it is a public facing server then why a dynamic IP and not static and why not use dynamic DNS ?

If it is a home router then again just use Dynamic DNS

or am i missing a point ?

Cheers

---

### Post by stlu on 2012-02-14
I have an agreement to make use of another computer behind a router for educational use.  That ISP provides a dynamic IP.

If by "dynamic DNS" you mean the service where a person manually updates their IP address with a site that redirects a host, such as *myhost.no-ip.com*, I do that on my end, but the problem is it won't work unless I know the IP address in the first place.  I can find out my IP locally from a site like "whatismyip.com,"  I cannot do this with the remote machine, as I cannot access it once the IP changes.

So what I need is, when the remote machine's script pulls the new IP from that website, it needs to send it to my IP or my host redirect.  Just a plain text.  If I open an NFS server on my machine, I could have the remote machine mount my home folder and create a new file with the remote IP in it, that way I could keep track of it.  While security is not a huge issue on my end, as my pc is specifically set up just for educational use, I know that setting up a default NFS server open to the internet is really going to be insecure.

So, what is a better way to pass that message to my machine?

---

### Post by SlugSlug on 2012-02-14
> **stlu said:**
> I have an agreement to make use of another computer behind a router for educational use.  That ISP provides a dynamic IP.

If by "dynamic DNS" you mean the service where a person manually updates their IP address with a site that redirects a host, such as *myhost.no-ip.com*, I do that on my end, but the problem is it won't work unless I know the IP address in the first place.  I can find out my IP locally from a site like "whatismyip.com,"  I cannot do this with the remote machine, as I cannot access it once the IP changes.

So what I need is, when the remote machine's script pulls the new IP from that website, it needs to send it to my IP or my host redirect.  Just a plain text.  If I open an NFS server on my machine, I could have the remote machine mount my home folder and create a new file with the remote IP in it, that way I could keep track of it.  While security is not a huge issue on my end, as my pc is specifically set up just for educational use, I know that setting up a default NFS server open to the internet is really going to be insecure.

So, what is a better way to pass that message to my machine?

use dynamicDNS  with the dynDNS instaled on the machine, It will auto update the record when the machines IP changes 

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by stlu on 2012-04-09
I misunderstood "Dynamic DNS."  I thought I was already using it to its full capacity, but I was still manually updating my information personally.  Now I see that the software install will do all that for me.

Thank you

-self-teaching linux user

---

