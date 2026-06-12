---
title: "Mythbuntu 9.10 Alpha 5"
date: 2009-09-08
forum: Mythbuntu
---

### Post by dreweinhorn on 2009-09-08
Is this the right place to discuss issues with Mythbuntu 9.10 Alpha 5?
If not, where is the right place.

Not sure if my problem is with my hardware, upstream Ubuntu 9.10 Alpha 5?
Or Mythbuntu, specific.

Things fail before the installer is up and running?

Is there a good technique for capturing error messages while the installer is starting up?  Maybe install in a Virtualbox VM and use recordmydesktop
to capture video of the running installer, pause the video to copy the messages by hand.  Or is there an easier way.

I have a vanilla Ubuntu 9.10 Alpha 5 iso downloading at the moment.  Will see if I get the same results with it.

It would be easier to avoid  confusion if the mythbuntu alpha .isos had
mythbuntu in the name instead of having the same name as the ubuntu alpha isos.

---

### Post by superm1 on 2009-09-08
> **dreweinhorn said:**
> Is this the right place to discuss issues with Mythbuntu 9.10 Alpha 5?
If not, where is the right place.


Depends on the specifics of your issue.  If they're bugs, No, file a bug  report.  if general feedback, things you want changed etc, then yes here.

> 
Not sure if my problem is with my hardware, upstream Ubuntu 9.10 Alpha 5?
Or Mythbuntu, specific.

Things fail before the installer is up and running?

How do they fail?  No graphics?  

> 
Is there a good technique for capturing error messages while the installer is starting up?  Maybe install in a Virtualbox VM and use recordmydesktop
to capture video of the running installer, pause the video to copy the messages by hand.  Or is there an easier way.

I have a vanilla Ubuntu 9.10 Alpha 5 iso downloading at the moment.  Will see if I get the same results with it.

It would be easier to avoid  confusion if the mythbuntu alpha .isos had
mythbuntu in the name instead of having the same name as the ubuntu alpha isos.
File a bug for installer related bugs with this tool:

```
ubuntu-bug ubiquity
```

It will attach all the appropriate logs as necessary.

---

### Post by dreweinhorn on 2009-09-08
> **superm1 said:**
> Depends on the specifics of your issue.  If they're bugs, No, file a bug  report.  if general feedback, things you want changed etc, then yes here.


How do they fail?  No graphics?  


File a bug for installer related bugs with this tool:

```
ubuntu-bug ubiquity
```

It will attach all the appropriate logs as necessary.


The iso file names need to be changed to something that really describes the iso.

Should be:

   mythbuntu-karmic-desktop-alpha-5-i386.iso, or
   mythbuntu-karmic-desktop-alpha-5-amd64.iso

not:

   karmic-desktop-i386.iso, or
   karmic-desktop-amd64.iso

which is easily confused with all the other karmic desktop versions.

I'm seeing a couple of different failures.

I'll file bug reports once I succeed in capturing all the logs, etc.

But first I'll describe the hardware.  

It's a Intel Core 2 Duo E7400, in a Asus P5N7A-VM motherboard with 4GB in
2 modules MEM 2Gx2|OCZ DII800 OCZ2P8004GK R

I got ahead of myself and there are a pair of Hauppage 1600 pci cards in the box.  I need to pull them before the next test.

I can boot the installer from CD or USB and run memory diagnostics with no problems.

Verifying the installation media fails.  The mythbuntu logo, etc. comes up, a progress thermometer moves from the left all the way to the right,
and just hangs.  No success or failure message the usb activity light is on solid.  I was interrupted and left the box a couple hours ago.

I tried verifying the installation after burning a cd a while ago and had similar results, the ide cd/dvd drive has been gathering quite a bit of dust on the shelf, and I don't really trust it, a new sata cd/dvd writer is on order.

The only drive plugged into the system is a 80GB WD IDE drive.

When I try to do an install from usb I get lots of complaints about the non-existent fd0 floppy failing.  Then some messages that go by too fast to read them.  I could try harder next time.  But I'm sure I'll still miss some.  X fails to start.  I get a console login.  Try to log in a root with no password.  But this fails.  Need to get a shell prompt before I can do the:  

   ubuntu-bug ubiquity

What is the default root password before the installer has set up any real accounts or passwords.

---

### Post by tgm4883 on 2009-09-08
> **dreweinhorn said:**
> The iso file names need to be changed to something that really describes the iso.

Should be:

   mythbuntu-karmic-desktop-alpha-5-i386.iso, or
   mythbuntu-karmic-desktop-alpha-5-amd64.iso

not:

   karmic-desktop-i386.iso, or
   karmic-desktop-amd64.iso

which is easily confused with all the other karmic desktop versions.



Yes, thank you for that. When we officially release an alpha for the karmic cycle I will be sure to use the same naming scheme that we have been using for every other pre-release that we have done. The naming scheme is as below.

mythbuntu-9.10-beta-desktop-amd64.iso


If you have a problem with how they are named after canonical builds them, please file a bug with them, as they are the one that name it when built. Once you see it listed on our site, rest assured, that it will have the above name scheme.

---

### Post by dreweinhorn on 2009-09-09
> **tgm4883 said:**
> Yes, thank you for that. When we officially release an alpha for the karmic cycle I will be sure to use the same naming scheme that we have been using for every other pre-release that we have done. The naming scheme is as below.

mythbuntu-9.10-beta-desktop-amd64.iso


If you have a problem with how they are named after canonical builds them, please file a bug with them, as they are the one that name it when built. Once you see it listed on our site, rest assured, that it will have the above name scheme.

Please start with this naming convention with alpha 6.
If, there is going to be an alpha 6.

Or, mythbuntu-10.4-alpha-1-i386.iso, if that's the next alpha version.

---

### Post by superm1 on 2009-09-09
> **dreweinhorn said:**
> The iso file names need to be changed to something that really describes the iso.

Should be:

   mythbuntu-karmic-desktop-alpha-5-i386.iso, or
   mythbuntu-karmic-desktop-alpha-5-amd64.iso

not:

   karmic-desktop-i386.iso, or
   karmic-desktop-amd64.iso

which is easily confused with all the other karmic desktop versions.

I'm seeing a couple of different failures.

I'll file bug reports once I succeed in capturing all the logs, etc.

But first I'll describe the hardware.  

It's a Intel Core 2 Duo E7400, in a Asus P5N7A-VM motherboard with 4GB in
2 modules MEM 2Gx2|OCZ DII800 OCZ2P8004GK R

I got ahead of myself and there are a pair of Hauppage 1600 pci cards in the box.  I need to pull them before the next test.

I can boot the installer from CD or USB and run memory diagnostics with no problems.

Verifying the installation media fails.  The mythbuntu logo, etc. comes up, a progress thermometer moves from the left all the way to the right,
and just hangs.  No success or failure message the usb activity light is on solid.  I was interrupted and left the box a couple hours ago.

I tried verifying the installation after burning a cd a while ago and had similar results, the ide cd/dvd drive has been gathering quite a bit of dust on the shelf, and I don't really trust it, a new sata cd/dvd writer is on order.

The only drive plugged into the system is a 80GB WD IDE drive.

When I try to do an install from usb I get lots of complaints about the non-existent fd0 floppy failing.  Then some messages that go by too fast to read them.  I could try harder next time.  But I'm sure I'll still miss some.  X fails to start.  I get a console login.  Try to log in a root with no password.  But this fails.  Need to get a shell prompt before I can do the:  

   ubuntu-bug ubiquity

What is the default root password before the installer has set up any real accounts or passwords.
Try user "ubuntu", no password.

---

### Post by tgm4883 on 2009-09-09
> **dreweinhorn said:**
> Please start with this naming convention with alpha 6.
If, there is going to be an alpha 6.

Or, mythbuntu-10.4-alpha-1-i386.iso, if that's the next alpha version.

Yes when the Mythbuntu team officially releases a pre-release version of Mythbuntu 9.04 (which means that you are using an unapproved pre-release) it will be named mythbuntu-9.10-alpha6-i386.iso.  Not because you say so, but because that is what we have always done. Now please, stop complaining to us about Canonical's naming process, something that we have no control over. If you download the ISO from Mythbuntu.org and it is named incorrectly, then let me know.

---

### Post by dreweinhorn on 2009-09-10
> **tgm4883 said:**
> Yes when the Mythbuntu team officially releases a pre-release version of Mythbuntu 9.04 (which means that you are using an unapproved pre-release) it will be named mythbuntu-9.10-alpha6-i386.iso.  Not because you say so, but because that is what we have always done. Now please, stop complaining to us about Canonical's naming process, something that we have no control over. If you download the ISO from Mythbuntu.org and it is named incorrectly, then let me know.

So far all I have been able to find on mythbuntu.org are stale,
stale jaunty 9.04 alphas.

Googling: site:mythbuntu.org karmic alpha
does not return anything at all.

I am not complaining about the naming Canonical's conventions for  official pre-releases.  I think it is right on.

I am complaining about your naming convention, or lack thereof, for unofficial prereleases.

Can you explain why the current 64-bit alpha 5 in

     [http://cdimage.ubuntu.com/mythbuntu/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/mythbuntu/releases/karmic/alpha-5/)

is named:

     karmic-desktop-amd64.iso

instead of:

     mythbuntu-9.10-alpha5-amd64.iso

This name indicates what it is.  

karmic-desktop-amd64.iso could be a lot of different things.
It is confusing and completely unnecessary. 

Why do you like the name karmic-desktop-amd64.iso?

---

### Post by dreweinhorn on 2009-09-10
> **superm1 said:**
> Try user "ubuntu", no password.

That works, thanks!

Running:

   ubuntu-bug ubiquity

does builds some then invokes what appears to be an html form,
with a text based browser.  Unfortunately when I tab over to the
username/password fields and try to enter my launchpad username/password.
I get stuck and nothing happens.  

Sometimes the console is bombarded with repetitive messages every couple seconds which makes it hard to interact with these scripts.

alpha5 is not working with my hardware and I really want to get it submitted in hopes for a better alpha6.

---

### Post by tgm4883 on 2009-09-10
> **dreweinhorn said:**
> So far all I have been able to find on mythbuntu.org are stale,
stale jaunty 9.04 alphas.


Exactly why I said you were using unofficial alphas, you didn't get them through the Mythbuntu website.

> 
Googling: site:mythbuntu.org karmic alpha
does not return anything at all.


Thats because there is not an official mythbuntu 9.10 alpha 5

> 
I am not complaining about the naming Canonical's conventions for  official pre-releases.  I think it is right on.


Yes you are, and you don't even know it.

> 
I am complaining about your naming convention, or lack thereof, for unofficial prereleases.


No, you are complaining about canonicals naming convention (or rather the naming convention that is in place on ubuntu build servers)

> 
Can you explain why the current 64-bit alpha 5 in

     [http://cdimage.ubuntu.com/mythbuntu/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/mythbuntu/releases/karmic/alpha-5/)

is named:

     karmic-desktop-amd64.iso

instead of:

     mythbuntu-9.10-alpha5-amd64.iso

This name indicates what it is.  

karmic-desktop-amd64.iso could be a lot of different things.
It is confusing and completely unnecessary. 


yes, because cdimage.ubuntu.com != [www.mythbuntu.org](www.mythbuntu.org), how do I have any control over what they name it at cdimage.ubuntu.com servers? I am not a canonical employee.

> 
Why do you like the name karmic-desktop-amd64.iso?

I don't, when I decide to release an alpha for 9.10, i'll rename it.  When I do, guess what, it will be listed on [www.mythbuntu.org](www.mythbuntu.org).


Just for fun, why don't you take a look at the naming convention at the following links, then decide if you are complaining to the right person.

[http://cdimage.ubuntu.com/ubuntustudio/daily/current/](http://cdimage.ubuntu.com/ubuntustudio/daily/current/)
[http://cdimage.ubuntu.com/kubuntu/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/kubuntu/releases/karmic/alpha-5/)
[http://cdimage.ubuntu.com/xubuntu/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/xubuntu/releases/karmic/alpha-5/)

---

### Post by dreweinhorn on 2009-09-10
> **dreweinhorn said:**
> That works, thanks!

Running:

   ubuntu-bug ubiquity

does builds some then invokes what appears to be an html form,
with a text based browser.  Unfortunately when I tab over to the
username/password fields and try to enter my launchpad username/password.
I get stuck and nothing happens.  

Sometimes the console is bombarded with repetitive messages every couple seconds which makes it hard to interact with these scripts.

alpha5 is not working with my hardware and I really want to get it submitted in hopes for a better alpha6.

Ok, 
I booted the alpha5 iso from cd.
I chose the option to try without installing.
X failed to start.
I got a login prompt on the console.
I logged in as ubuntu with no password
I ran:  ubuntu-bug ubiquity
I chose the option to save a copy of the report, because automatically submitting was not working for me.

Can you point me to the right place to submit it.

Is there any other information I should include,
perhaps a demesg?

Vanilla Jaunty Ubuntu installs without problem in both 32-bit and 64-bit versions on this box.

Verifying the distribution media works for Jaunty,
with all karmic versions when I try to verify the installation media, 
it hangs with reporting either success or failure.
Should I file a bug report about this?

Sometimes, not always I get repeated complaints about:

unable to enumerate USB device on port 2,
and
connect bounce failed, port 2 disabled.

The only currently connected usb device is a garden variety usb mouse.

---

