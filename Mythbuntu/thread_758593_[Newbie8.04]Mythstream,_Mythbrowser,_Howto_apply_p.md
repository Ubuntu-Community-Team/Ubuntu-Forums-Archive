---
title: "[Newbie/8.04]Mythstream, Mythbrowser, Howto apply patches?"
date: 2008-04-18
forum: Mythbuntu
---

### Post by Stevi on 2008-04-18
Hi,

I'm new to Mythbuntu. It's really great. Hopefully you can answer my three questions:
[LIST=1]
[*]Is it possible to listen to Online-Streams via Mythstream while leaving the Mythstream-Menu? Like it can be done with Mythmusic?
[*]Are you able to change the www-application from Mythbrowser to Firefox in Mythbuntu 8.04 Beta? This doesn't work for me. I followed [these instructions (Link)](http://www.mythtv.org/wiki/index.php/Firefox) but when I click an url nothing happens.
[*]I am not able to view EPG from within live-TV. I found [a fix for this(Link)](http://svn.mythtv.org/trac/ticket/4964). Does anybody know a How-To that describes how to apply a .patch-file to Mythbuntu? (I'm totally new to this!)
[/LIST]

Thanks in advance

Stevi.

---

### Post by superm1 on 2008-04-18
> **Stevi said:**
> Hi,

I'm new to Mythbuntu. It's really great. Hopefully you can answer my three questions:[LIST=1]
[*]Is it possible to listen to Online-Streams via Mythstream while leaving the Mythstream-Menu? Like it can be done with Mythmusic?[/LIST]

The architecture of mythstream i don't believe allows this.  You can talk to it's developer and see if he is willing to add it though.

> 
[LIST=1]
[*]Are you able to change the www-application from Mythbrowser to Firefox in Mythbuntu 8.04 Beta? This doesn't work for me. I followed [these instructions (Link)]("http://www.mythtv.org/wiki/index.php/Firefox") but when I click an url nothing happens.[/LIST]
I've been able to do this without trouble.  Check "behind" myth in case it did start somewhere that you didn't expect.  Also look at /var/log/mythtv/mythfrontend.log for information on errors it is encountering.

> 
[LIST=1]
[*]I am not able to view EPG from within live-TV. I found [a fix for this(Link)]("http://svn.mythtv.org/trac/ticket/4964"). Does anybody know a How-To that describes how to apply a .patch-file to Mythbuntu? (I'm totally new to this!)[/LIST]

Rough overview of how to apply a local patch:

1) apt-get build-dep mythtv
2) apt-get source mythtv
3) apt-get install devscripts
4) dch -i  (put some comments in about what you changed.  In the version number, use the old version number plus a +local1 or something similar.  This will make sure that you're version is marked newer, but that if an even "newer" version came out, you can still get it.
5) Try to apply the patch.  If it applies cleanly, unapply it and put it in debian/patches.
6) Update the debian/patches/00list to include the patch
7) debuild
8) You should get some binaries out.
9) File a bug for the inclusion of this patch on the Ubuntu bug tracker.

Thanks in advance

Stevi.[/quote]

---

### Post by mrand on 2008-04-18
> **superm1 said:**
> 
Rough overview of how to apply a local patch:

1) apt-get build-dep mythtv
2) apt-get source mythtv
3) apt-get install devscripts
4) dch -i  (put some comments in about what you changed.  In the version number, use the old version number plus a +local1 or something similar.  This will make sure that you're version is marked newer, but that if an even "newer" version came out, you can still get it.
5) Try to apply the patch.  If it applies cleanly, unapply it and put it in debian/patches.
6) Update the debian/patches/00list to include the patch
7) debuild
8) You should get some binaries out.
9) File a bug for the inclusion of this patch on the Ubuntu bug tracker.

Thanks in advance

Stevi.

Since the title is newbie and is asking a build question, I hope you don't mind me asking a follow-up - since I'm a newbie at building.

What version of mythtv source does the above retrieve?  Since it doesn't say otherwise, I'm guessing it's the mythbuntu "trunk source", which I assume at this point is 0.21.  Is there a way to ensure that the pulled source stays at 0.21 and doesn't go to 0.22 at some point in time (at least, not until 0.22 is about to be released)?

If my terms and/or concepts are confused, PLEASE correct me.  Hopefully it's obvious what I'm wanting to do: be able to easily get any upstreams fixes to 0.21 while being able to play with that source.

While I'm asking, would there be any benefit to upgrading to Mythbuntu 8.04 first, before switching over to doing the source-based builds (in terms of ease of transitioning from Mythbuntu 7.10)?

   Marc

---

### Post by Stevi on 2008-04-18
Thx Superm!
> **superm1 said:**
> The architecture of mythstream i don't believe allows this.  You can talk to it's developer and see if he is willing to add it though.
I wrote an e-mail to the developer.
> **superm1 said:**
> I've been able to do this without trouble.
I think it's [this error](http://blog.zenone.org/2008/03/firefox-within-mythtv.html). But the fix
> **"Steve Zenone"]The quick solution was to create a simple script that acts as a wrapper to filter out those options. Simply do the following to create the wrapper (I was using tcsh when I did the following...use whatever you want said:**
> 
doesn't work on my machine. Maybe there are some file-permission problems :confused:

[QUOTE=superm1;4740436]
Rough overview of how to apply a local patch: (...) 
Thanks for this. I'll try.

---

### Post by lessfield on 2008-07-15
> 
doesn't work on my machine. Maybe there are some file-permission problems 

I use a slightly different "wrapper".
First, need to install firefox extension autohide
[http://www.krickelkrackel.de/autohide/]("http://www.krickelkrackel.de/autohide/")
then create a script /usr/bin/firefox-wrapper 
```
sudo echo "/usr/bin/firefox -fullscreen $11"
/usr/bin/firefox -fullscreen $11
exit 0 

```
and set the permissions 

```

sudo chmod 755 /usr/bin/firefox-wrapper
sudo chown "MYTHTV_USER" /usr/bin/firefox-wrapper

```
where MYTHTV_USER is your myth user name.

---

### Post by Stevi on 2008-07-24
Thank you. This works for me. :)
Are you able to navigate through webpages using the remote control or are you using a mouse?

---

### Post by lessfield on 2008-07-29
I use a wireless keyboard and i control the pointer with the number pad

---

### Post by mxander on 2010-01-10
I've tried to apply a patch to solve the issue described in the ticket 7515:
"SRT subtitle timings wildly variable"
[http://svn.mythtv.org/trac/ticket/7515](http://svn.mythtv.org/trac/ticket/7515)
But I cannot manage to follow the first step of you Howto:

sudo apt-get build-dep mythtv
[sudo] password for MyUserName: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have unmet dependencies:
  nvidia-185-libvdpau-dev: Depends: nvidia-185-libvdpau (>= 185.18.36) but it is not going to be installed
E: Build-dependencies for mythtv could not be satisfied.

---

