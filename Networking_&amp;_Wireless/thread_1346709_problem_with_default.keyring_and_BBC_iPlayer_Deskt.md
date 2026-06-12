---
title: "problem with default.keyring and BBC iPlayer Desktop"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by markling on 2009-12-05
I'm unable to remember my horribly complicated default keyring password.

This does not only mean I cannot use BBC iPlayer Desktop.

It has also unearthed a number of other problems with the default keyring.

(see 'scenario' at the end of this message for context and background to this problem)

1. The password gui doesn't tell me that I have entered the wrong password
--------------------------------------------------------------------------

I know I entered the wrong password because it says so in the auth.log. At least I think that's what this means:

-
Dec  5 14:59:22 mark-laptop gnome-keyring-ask: could not grab keyboard: 3
-

But when I enter the wrong default.keyring password in the dialogue that asks for it, nothing happens. The dialogue goes away. But it doesn't tell me I've entered a wrong password.

2. The password gui doesn't allow me to try again
-------------------------------------------------

This is a problem when I've entered the wrong password. I would like to try again but it won't let me. I don't even know where to go to change my default.keyring password. I remember looking for somewhere to do this some months back but couldn't find it.

3. My default keyring is broken anyway
---------------------------------------

My default.keyring doesn't appear to be working at all. As I see now in the authlog entry when I start my computer:

--
Dec  2 10:16:14 mark-laptop gdm-session-worker[2012]: pam_unix(gdm:session): session opened for user mark by (uid=0)
Dec  2 10:16:14 mark-laptop gdm-session-worker[2012]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Dec  2 10:16:15 mark-laptop gnome-keyring-daemon[2083]: Couldn't unlock login keyring with provided password
Dec  2 10:16:15 mark-laptop gnome-keyring-daemon[2083]: Failed to unlock login on startup
Dec  2 10:16:22 mark-laptop seahorse-daemon[2171]: init gpgme version 1.1.8
--

Is this important? Has the security of my computer been compromised? What the heck is the default keyring anyway? And why didn't it tell me it wasn't working? Which brings us to...

4. System didn't tell me my keyring was broken
-----------------------------------------------
I suspect that since its been months since my computer asked my to enter my default keyring (when previously, I was being asked for it all the blooming time), then it has been months since my default.keyring was broken (I had assumed it had been civilized in an upgrade so that it didn't pester people so much).

This is a problem because if the system doesn't tell me the default.keyring is broken, how is it supposed to get fixed? This is also a problem, I would assume, because if leaves my computer vulnerable.

5. My default.keyring isn't even there
--------------------------------------
It's not merely defunct, its devoid!

I followed these helpful instructions in an attempt to reset my default.keyring password:

[http://ubuntuforums.org/showpost.php?p=943443&postcount=7](http://ubuntuforums.org/showpost.php?p=943443&postcount=7)

They recommend deleting the default.keyring file. But I do not have a default.keyring file. It's not in the location given in the instructions. It doesn't come up in a hidden-file-search of my home folder. (This default.keyring is like God: does it even exist at all? People keep talking about it. But no-one seems to know what it really is. It is omnipotent, apparently. But impotent to my day-to-day needs. I would appeal to it, if I knew where to find it. Go to the home folder, they said, you will find it there. I went to home folder but I couldn't find it. Is it me? Or is it not even there at all? Is everyone else pretending they find it when they go to the home folder because they are too scared to admit they didn't? Will people shoot me for daring to suggest that it doesn't exist at all?).

6. How do I fix my default.keyring? 
-----------------------------------
Assuming it exists, that is.

Scenario:
---------
This all became apparent when I tried to download a TV programme from the BBC iPlayer website. This would normally launch the BBC iPlayer Desktop application to handle the download. But instead of launching the application, my action causes the system to ask me for the default.keyring.

On entering my default.keyring incorrectly, nothing more happens. The iPlayer doesn't appear to launch. The Processes list in the System Monitor does list iPlayer as an active process. But I can't see any GUI action. There's nothing for me to click on. Nothing to use.

Here's a question: how come the BBC iPlayer is reliant on my default.kering working properly when I manage to do everything else (web, email) without it working at all?
 
Cheers

markling.

---

### Post by Fullmetal78 on 2011-04-03
> **markling said:**
> I'm unable to remember my horribly complicated default keyring password.

This does not only mean I cannot use BBC iPlayer Desktop.

It has also unearthed a number of other problems with the default keyring.

(see 'scenario' at the end of this message for context and background to this problem)

1. The password gui doesn't tell me that I have entered the wrong password
--------------------------------------------------------------------------

I know I entered the wrong password because it says so in the auth.log. At least I think that's what this means:

-
Dec  5 14:59:22 mark-laptop gnome-keyring-ask: could not grab keyboard: 3
-

But when I enter the wrong default.keyring password in the dialogue that asks for it, nothing happens. The dialogue goes away. But it doesn't tell me I've entered a wrong password.

2. The password gui doesn't allow me to try again
-------------------------------------------------

This is a problem when I've entered the wrong password. I would like to try again but it won't let me. I don't even know where to go to change my default.keyring password. I remember looking for somewhere to do this some months back but couldn't find it.

3. My default keyring is broken anyway
---------------------------------------

My default.keyring doesn't appear to be working at all. As I see now in the authlog entry when I start my computer:

--
Dec  2 10:16:14 mark-laptop gdm-session-worker[2012]: pam_unix(gdm:session): session opened for user mark by (uid=0)
Dec  2 10:16:14 mark-laptop gdm-session-worker[2012]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Dec  2 10:16:15 mark-laptop gnome-keyring-daemon[2083]: Couldn't unlock login keyring with provided password
Dec  2 10:16:15 mark-laptop gnome-keyring-daemon[2083]: Failed to unlock login on startup
Dec  2 10:16:22 mark-laptop seahorse-daemon[2171]: init gpgme version 1.1.8
--

Is this important? Has the security of my computer been compromised? What the heck is the default keyring anyway? And why didn't it tell me it wasn't working? Which brings us to...

4. System didn't tell me my keyring was broken
-----------------------------------------------
I suspect that since its been months since my computer asked my to enter my default keyring (when previously, I was being asked for it all the blooming time), then it has been months since my default.keyring was broken (I had assumed it had been civilized in an upgrade so that it didn't pester people so much).

This is a problem because if the system doesn't tell me the default.keyring is broken, how is it supposed to get fixed? This is also a problem, I would assume, because if leaves my computer vulnerable.

5. My default.keyring isn't even there
--------------------------------------
It's not merely defunct, its devoid!

I followed these helpful instructions in an attempt to reset my default.keyring password:

[http://ubuntuforums.org/showpost.php?p=943443&postcount=7](http://ubuntuforums.org/showpost.php?p=943443&postcount=7)

They recommend deleting the default.keyring file. But I do not have a default.keyring file. It's not in the location given in the instructions. It doesn't come up in a hidden-file-search of my home folder. (This default.keyring is like God: does it even exist at all? People keep talking about it. But no-one seems to know what it really is. It is omnipotent, apparently. But impotent to my day-to-day needs. I would appeal to it, if I knew where to find it. Go to the home folder, they said, you will find it there. I went to home folder but I couldn't find it. Is it me? Or is it not even there at all? Is everyone else pretending they find it when they go to the home folder because they are too scared to admit they didn't? Will people shoot me for daring to suggest that it doesn't exist at all?).

6. How do I fix my default.keyring? 
-----------------------------------
Assuming it exists, that is.

Scenario:
---------
This all became apparent when I tried to download a TV programme from the BBC iPlayer website. This would normally launch the BBC iPlayer Desktop application to handle the download. But instead of launching the application, my action causes the system to ask me for the default.keyring.

On entering my default.keyring incorrectly, nothing more happens. The iPlayer doesn't appear to launch. The Processes list in the System Monitor does list iPlayer as an active process. But I can't see any GUI action. There's nothing for me to click on. Nothing to use.

Here's a question: how come the BBC iPlayer is reliant on my default.kering working properly when I manage to do everything else (web, email) without it working at all?
 
Cheers

markling.

Have you fixed your issue?

---

### Post by markling on 2011-04-24
I fixed my issue by reinstalling the operating system. That way the default keyring could be reset. The same problem hasn't since arisen. I presume it's been fixed somewhere down the line. Who knows? God works in mysterious ways. Ours is not to know the reason why. Or if, or how. Though neither the keyring nor BBC iPlayer is perfect, I get through the day without any major breakdowns. The keyring could be made more user-friendly, the iPlayer could be made more stable. There could even one day be a purpose... to posting calls for support to forums.

---

