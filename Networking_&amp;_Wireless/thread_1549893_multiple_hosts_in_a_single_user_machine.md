---
title: "multiple hosts in a single user machine"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by spoilingmyself on 2010-08-10
Hey all, 

May be the title doesn't the convey the real issue, actually that is where the problem lies, I am unable to express my problem, therefore google or search here doesn't help!
I'll try to write what I am facing since more than a month now. How it started and to what extent I have solved. Please bear with me, as I am a /no+b/ 
The basic thing is when i start the system offline the terminal says:
neha@localhost:~$/
and every application seems to work as required..
But as soon as I am connected to any network, be it wired or wireless. the applications like rhythmbox break, vmware doesn't start or if is started, gives error on surfing the web pages.
the terminal reads:
neha@neha-laptop:~$ 
and to start vmware I have to enter- xhost SI:localuser:root
and rhythmbox has to be restarted again.
THis is very irritating at times. 
I have tried to edit to the /etc/hosts file but it doesn't help.
I think I need to change the place where this /etc/hosts is maintained, in that case /etc/host.conf shows multi off
I am unable to get the real problem short and google the solution, this place seems is the refuge!!
please help..

Appreciations in advance.

---

### Post by marc.verwerft on 2010-08-10
Have a look here: [http://jblevins.org/computing/linux/hostname](http://jblevins.org/computing/linux/hostname)
Maybe that helps you.

Regards,

Marc

---

### Post by spoilingmyself on 2010-08-10
> **marc.verwerft said:**
> Have a look here: [http://jblevins.org/computing/linux/hostname](http://jblevins.org/computing/linux/hostname)
Maybe that helps you.

Regards,

Marc

Yeah, Thanks Marc.

---

### Post by capscrew on 2010-08-11
> **spoilingmyself said:**
> ...
The basic thing is when i start the system offline the terminal says:
neha@localhost:~$/
and every application seems to work as required..
But as soon as I am connected to any network, be it wired or wireless. the applications like rhythmbox break, vmware doesn't start or if is started, gives error on surfing the web pages.
the terminal reads:
neha@neha-laptop:~$ 
Post the following```
/etc/hosts
/etc/hostname
/etc/resolv.conf
```
What version of Ubuntu are you using?> 
and to start vmware I have to enter- xhost SI:localuser:root
and rhythmbox has to be restarted again.
THis is very irritating at times. 
I have tried to edit to the /etc/hosts file but it doesn't help.
I think I need to change the place where this /etc/hosts is maintained,
In Ubuntu's standard configuration /etc/hosts is edited directly >  in that case /etc/host.conf shows multi off
/etc/host.conf (note this is ***not hosts***)  does not update the /etc/hosts file.  See [**_here _**]("http://www.faqs.org/docs/securing/chap5sec39.html").  it merely tells the resolver libs which method to use.  It is not used in later Ubuntu versions. > 
I am unable to get the real problem short and google the solution...
This seems like a [**_logical starting point_**]("http://www.google.com/search?hl=en&q=etc+host.conf+use&aq=f&aqi=&aql=&oq=&gs_rfai=").

---

### Post by spoilingmyself on 2010-08-11
sudo hostname [xxxx]
sudo /etc/init.d/hostname.sh

executing these two consecutively does what I want but temporarily, unlike what was written in the link above.. 
and after this the host changes therefore, like it used to happen when I got online, the x server needs to be told that I am the same user by running xhost SI:[xxxx]:local
and the rhythmbox, one application that breaks, has to be restarted.

So, it seems the problem lies there, why are there two users on the machine that is used by a single user, thats me. 
The links given were sure quite enriching, but it feels that I am not being rational reading those, I am actually getting irritated and that has blocked my vision, perhaps.

I would be quite thankful to suggestions that provide a fix for this or an explanation as to why this is happening.
I know I am being stupid, and utterly unpleasant.. Hope someone could understand my state of mind.

---

### Post by marc.verwerft on 2010-08-12
At boot time the hostname of your computer is set to whatever is in /etc/hostname. Maybe you named it localhost instead of neha-laptop?

From the man page of hostname:
      -b, --boot
              Always set a hostname; this allows the file specified by  -F  to
              be  non-existant  or  empty,  in which case the default hostname
              localhost will be used if none is yet set.

Hope this is getting you closer to the problem.

Regards,

Marc

---

