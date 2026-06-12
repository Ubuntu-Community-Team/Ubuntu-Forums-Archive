---
title: "Mythgallery stops with slideshow"
date: 2010-01-08
forum: Mythbuntu
---

### Post by warti on 2010-01-08
Hello,

I have the problem, that the Mythgallery stops the slideshow after about 7 pictures.(Note: each row contains 7 pictures). :(

If I start mythfrontend manually - using the same account - it works :confused:

My environment:

Mythfrontend running on a small HTPC - Athlon2.4 GHz, Nvidia 4MX using Mythbuntu 9.10. I mounted the pictures via a samba share.

My server is a Debian Lenny System, running myth-backend 0.22.

I attached the Loggings containing the "Problem.txt" and the good version "NoProblem.txt" in one zip-file

Does anyone have the same problem? Does anybody have any ideas to fix this problem?

Regards,
Werner

---

### Post by warti on 2010-01-12
Hello again,

may I answer on my own problem ;)

The problem was that the DPMS functionality stopped somehow the "slideshow".
After switching off DPMS it works without problems. For me this is solved
because my old TV-Set does not care about DPMS at all.

Regards,
Werner

---

### Post by heisti on 2010-01-13
> **warti said:**
> Hello again,

may I answer on my own problem ;)

The problem was that the DPMS functionality stopped somehow the "slideshow".
After switching off DPMS it works without problems. For me this is solved
because my old TV-Set does not care about DPMS at all.

Regards,
Werner
How did you do that? Where is the place where i can find that "DPMS"?

---

### Post by warti on 2010-01-13
Normaly one should put *option "DPMS" "OFF"* somewhere  in the "xorg.conf" to switch it off. But for any reason this does not work.

So I put "xset -dpms"  into the mythfrontend start script:
/usr/bin/mythfrontend

Regards,
Werner

---

### Post by heisti on 2010-01-14
> **warti said:**
> Normaly one should put *option "DPMS" "OFF"* somewhere  in the "xorg.conf" to switch it off. But for any reason this does not work.

So I put "xset -dpms"  into the mythfrontend start script:
/usr/bin/mythfrontend

Regards,
Werner
That did't work for me.
I solved my problem by adding /usr/bin/mythfrontend to sudoers file. Then I added sudo to mythwelcome startup command.
Tadaa, now it works, but mythfrontend run allways root rights.
What do you think about that?

-Timppa-

---

### Post by warti on 2010-01-14
Did you also (have/had) problems with mythgallery and the slideshow??

---

### Post by heisti on 2010-01-14
Yes, I had those problems. 
Slideshow stops after every 6th picture, but starts again when I push "p" button on keyboard.

-Timppa-

---

### Post by warti on 2010-01-14
Ahhh - And I thought I was the only one ;)

Best regards,
Werner

---

### Post by UrsSchmitzli on 2010-01-15
Hi,

I have the same problem that mythgallery's slideshow stops after a varying number of photos. I tried the DPMS option, but without success.

The other suggestion
```
sudo mythfrontend
```solves the problem, but I really don't want to run mythfrontend with root privileges.  :-k

Do you have an idea why the slideshow stops when running mythfrontend without root privileges? Maybe some file/folder permissions?

@warti: Could you please remove the [SOLVED] tag from this thread? So far, we have one possible solution (DPMS), but that doesn't always help...

---

### Post by warti on 2010-01-15
> @warti: Could you please remove the [SOLVED] tag from this thread? So far, we have one possible solution (DPMS), but that doesn't always help...                                                                                                                   Unsolving - Done. 

You can check for DPMS state with the following command: xset q

MfG
Werner

*EDIT* This thread [http://ubuntuforums.org/showthread.php?t=1381521](http://ubuntuforums.org/showthread.php?t=1381521) is about switching off dpms ...

---

### Post by heisti on 2010-01-15
If you find a solution, let us know.
I'm also worried about using root privileges, but I have to use that so far until the solution is figured out.

---

### Post by warti on 2010-01-15
> I'm also worried about using root privileges, but I have to use that so far until the solution is figured out.     Strange, my mythfrontend is running with limited rights:
```

ps -ef

.....
werner    1511     1  0 21:17 ?        00:00:00 xfdesktop
werner    1517     1 10 21:17 ?        00:00:23 /usr/bin/mythfrontend.real --logfile /var/log/mythtv/mythfr
....

```I changed "/usr/bin/mythfrontend" like that:
```
#find the session, dialog, and su manager we will be using for display
find_session
find_dialog
find_su

#check that we are in the mythtv group
check_groups

[U]xset -dpms
[/U]
#create a symbolic link for mysql.txt so it can't be overwritten
mkdir -p $HOME/.mythtv
if [ ! -e $HOME/.mythtv/mysql.txt ]; then

```Werner

---

### Post by UrsSchmitzli on 2010-01-18
Here is my solution:

```
sudo apt-get purge gnome-screensaver
```

---

