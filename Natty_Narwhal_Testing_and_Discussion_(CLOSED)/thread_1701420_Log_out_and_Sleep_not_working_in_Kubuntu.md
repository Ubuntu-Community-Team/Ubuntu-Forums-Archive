---
title: "Log out and Sleep not working in Kubuntu"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by PaulW2U on 2011-03-06
I've recently made a new installation of Kubuntu 11.04 and downloaded the latest KDE 4.61 updates. I have a surprisingly stable installation with very few crashes unlike my former Ubuntu/Unity 11.04 set-up. I like the improvements that have been made over the last year and would like to stick with this release if I can.

I have just two major problems:

[LIST]
[*]Log-out doesn't work. The main desktop is replaced by a black terminal screen. A small amount of text is displayed but no input is possible. I then need to switch to VT1 to issue a shutdown or reboot command
[*]Sleep or suspend - my screen goes blank but after several minutes the PC hasn't closed down and moving the mouse bring the display back into life.
[/LIST]

Are these known problems with KDE or Kubuntu or are they specific to my PC? I have made a search of Launchpad and the KDE bug site but I haven't seen anything specific to my problem. Thanks in advance.

---

### Post by PaulW2U on 2011-03-06
I know it's considered bad practice to follow up your own posts but in the last 30 minutes I've found workarounds for both these problems. :)

Firstly, the problem of not being able to log out was fixed by adding **TerminateServer=true** to the X-*-Core section of /etc/kde4/kdm/kdmrc. I found this on another forum.

Secondly, persistent Googling eventually led me to an issue reported on these forums in connection with network shares. As soon as I unmounted my networked hard drive, suspend or sleep worked flawlessly.

It only goes to prove that whatever problems you have, someone else will probably already have had them and hopefully documented the fix or workaround, you just have to search. I didn't have this problem with my now deleted Ubuntu installation nor do I with my existing Xubuntu installation. May be it was a bad Kubuntu install but now I just need to see if bugs have already been reported or whether I need to do that myself.

**[COLOR="Red"]Edit[/COLOR]**: Marking this thread as solved as workaround found

---

