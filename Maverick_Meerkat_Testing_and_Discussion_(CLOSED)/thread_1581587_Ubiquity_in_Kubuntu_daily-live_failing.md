---
title: "Ubiquity in Kubuntu daily-live failing"
date: 2010-09-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2010-09-25
Confirmed gnome user here, but I thought I would see how Kubuntu Maverick was coming along. I downloaded the 24-Sept daily-live 64-bit ISO, but ubiquity fails to run. Trying to start the installer from the desktop or from the menu, the little icon bounces for a few moments and then nothing. Tried from the terminal, but no error messages, simply a short delay and the reappearance of the prompt.

Downloaded the 25-Sept ISO this morning and seeing the same. This bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/627489](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/627489)

... says (post #4):

> This bug was fixed in the package ubiquity - 2.3.11The ubiquity version in the 25-Sept CD was 2.4.1. I didn't investigate any deeper in the live session (I'm posting from gnome Maverick now) so this might be a separate issue, but I wondered if anyone else has tried the Kubuntu dailies and whether they're seeing the same.

Yes, I did check the md5sums and I tried both live-CD and live-USB with the 24-Sept ISO, and I unchecked the persistence option when making the 25-Sept USB in case this was the problem.

---

### Post by coffeecat on 2010-09-25
This bug seems more appropriate:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/646827](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/646827)

Looks as though they're onto the case.

---

### Post by VMC on 2010-09-25
> **coffeecat said:**
> This bug seems more appropriate:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/646827](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/646827)

Looks as though they're onto the case.

I "me too" the report, thanks.

I noticed that start kubuntu goes straight to livecd and passes any options, even though F6 reveals "...maybe-ubiquity...."

---

### Post by coffeecat on 2010-09-25
> **VMC said:**
> I noticed that start kubuntu goes straight to livecd and passes any options

With the 24-Sept ISO the live CD took me straight to the desktop, but a live USB prepared from the same ISO gave me the options. However, whichever option I selected I was presented with the log in screen and "ubuntu" and a blank password wouldn't log me in. I didn't think to try 'kubuntu' as a log in name.

Strange that the live CD and live USB should behave differently.

---

### Post by coffeecat on 2010-09-27
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/646827](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/646827) now says:

[quote="post #3"]This bug was fixed in the package ubiquity - 2.4.2[/quote]

I can confirm that. I remade a live USB from the 25-Sept ISO, but this time with a persistence file and did 'sudo apt-get update' and sudo 'apt-get upgrade' to get the 2.4.2 ubiquity. The live USB needed rebooting because ubiquity did open but crashed at first. On rebooting I got the chooser rather than going straight into the desktop. This time ubiquity worked OK and now I'm posting from Kubuntu Maverick on my HD. A few little niggles before it would work properly, but easily fixed.

The only thing now is to work out how to use this bizarre thing called KDE. I accidentally clicked on the X on that weird little virtual desktop and now it seems to have gone forever. :sigh: Never mind. It was always going to be a learning experience for me.

I would guess that ubiquity in the daily lives from tomorrow should work OK.

---

### Post by VMC on 2010-09-27
> **coffeecat said:**
> [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/646827](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/646827) now says:



I can confirm that. I remade a live USB from the 25-Sept ISO, but this time with a persistence file and did 'sudo apt-get update' and sudo 'apt-get upgrade' to get the 2.4.2 ubiquity. The live USB needed rebooting because ubiquity did open but crashed at first. On rebooting I got the chooser rather than going straight into the desktop. This time ubiquity worked OK and now I'm posting from Kubuntu Maverick on my HD. A few little niggles before it would work properly, but easily fixed.

The only thing now is to work out how to use this bizarre thing called KDE. I accidentally clicked on the X on that weird little virtual desktop and now it seems to have gone forever. :sigh: Never mind. It was always going to be a learning experience for me.

I would guess that ubiquity in the daily lives from tomorrow should work OK.

I just used todays (09-27-2010) ISO, and it stills fails to bring up choice of install or try. It goes straight to desktop and clicking install, I just see a spinning cursor and then it dies. I will re-check later looking if any error messages in /var/installer. This same symptom has occurred for the past 4 or 5 iso's.

---

### Post by coffeecat on 2010-09-27
> **VMC said:**
> I just used todays (09-27-2010) ISO, and it stills fails to bring up choice of install or try. It goes straight to desktop and clicking install, I just see a spinning cursor and then it dies. I will re-check later looking if any error messages in /var/installer. This same symptom has occurred for the past 4 or 5 iso's.

If you want to use the 27-Sept ISO, see which version of ubiquity comes with it. The 2.4.2 version probably just missed it. You could do what I did if you're using a live USB with persistence and update the system. You may only need to update ubiquity and its dependencies rather than a full system update, but I only had to download about 40MB for a full one.

---

### Post by VMC on 2010-09-27
> **coffeecat said:**
> If you want to use the 27-Sept ISO, see which version of ubiquity comes with it. The 2.4.2 version probably just missed it. You could do what I did if you're using a live USB with persistence and update the system. You may only need to update ubiquity and its dependencies rather than a full system update, but I only had to download about 40MB for a full one.

Yes, its 2.4.1. I mistakenly thought that was the latest version. I must have misread that bug report.

 I will try liveusb again then update ubiquity and see if I can pull in 2.4.2.

Edit: No, I can't update ubiquity to 2.4.2. I guess it hasn't been pushed out to the repositories.
 I'll wait and try again tomorrow, unless I can find it somewhere else.

Edit2: OK, I did a hatchet job, but finally got ubiquity updated - now its version 2.4.3. 
I was able to install Kubuntu. It least I now know it will install.
I didn't want to use persistence since I will be using tomorrows zsync ISO anyway.

---

### Post by SeijiSensei on 2010-09-27
Glad to see I wasn't crazy.  I know it's a daily build, but I certainly didn't expect the installer not to work!  Guess I go download the beta and start from there.

---

### Post by SeijiSensei on 2010-09-28
This bugs still exists in this morning's daily build for the amd64 architecture.  I noticed that the bug report only mentioned the i386 architecture.  I posted a [comment]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/646827/comments/4") on Launchpad asking whether the fixes had been ported to the 64-bit architecture as well.

---

### Post by coffeecat on 2010-09-28
I'm surprised the daily builds have not got this yet, because upgrading an earlier daily build on a live USB with the 2.4.2 ubiquity enabled me to install the other day. So clearly the 2.4.2 ubiquity had got into the repos then. This was with the 64-bit version.

Unless another bug has bit.

---

### Post by VMC on 2010-09-28
> **SeijiSensei said:**
> This bugs still exists in this morning's daily build for the amd64 architecture.  I noticed that the bug report only mentioned the i386 architecture.  I posted a [comment]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/646827/comments/4") on Launchpad asking whether the fixes had been ported to the 64-bit architecture as well.

Todays - maverick-desktop-amd64.iso 28-Sep-2010 11:37  695M, found [**_here_**]("http://cdimage.ubuntu.com/kubuntu/daily-live/current/maverick-desktop-amd64.iso"), worked for me using amd64.

---

### Post by SeijiSensei on 2010-09-28
Mine is dated 1:49 am.  I'll try yours and see if it works.  I'm installing in a Virtualbox VM after burning three or four CD "coasters" over the past couple of days.

Update:  Talk about a "moving target!"  Yes, the image now available does in fact install.

---

### Post by 67GTA on 2010-09-29
I just tried the Kubuntu daily image for the 28th (64bit), and the installer won't even open. The last two weeks of daily images only gave me partman errors.

---

