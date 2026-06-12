---
title: "Sporify in Xubuntu 18.04 in 2023?"
date: 2023-05-31
forum: Multimedia Software
---

### Post by Petr_Be on 2023-05-31
Hello,

we have a rather old computer with a 32-bit CPU in our bar slash community center. We are running Xubuntu 18.04 with Ubuntu Pro Free because 20.04 doesn't support 32-bit CPUs anymore.

Recently, the Spotify app has stopped allowing users to log in, because:

"Spotify says that the app is restricted to Premium users only because it has discontinued the support for older Spotify desktop application versions. If you're using a version of the Spotify desktop app that's older than 1.1.59, you won't be able to log in."

Is there a way to install the Spotify app 1.1.59 or newer in Xubuntu 18.04 32-bit?

The web version of Spotify is missing some features according to our users.

Thank you very much.

bhy

---

### Post by #&amp;thj^% on 2023-05-31
There is no 32-bit Spotify unfortunately. I looked into it and even when you do find a 32bit Spotify file somewhere, there will most likely be dependency issues (it wants libcurl3) and it's also an ancient client.

As an alternative, the [Spotify web player]("https://open.spotify.com/") should work just fine on your web browser. :KS

 

Hope this helps, have a nice day!

---

### Post by guiverc on 2023-05-31
Ubuntu 18.04 LTS is at *end of standard support*, and EOL for *i386* support & *armhf* or 32-bit.

Not all architectures have ESM or Ubuntu Pro options; *i386* for *bionic* or 32-bit x86 doesn't have ESM options, thus you won't be getting any benefit of Pro/ESM support as *i386* isn't an option for 18.04 ESM as not all architectures are supported.

> [Ubuntu Pro is available for *amd64, arm64, s390X*, and *PowerPC* architectures.]("https://ubuntu.com//blog/18-04-end-of-standard-support")

For more clues you may benefit from
- [https://ubuntu.com//blog/18-04-end-of-standard-support](https://ubuntu.com//blog/18-04-end-of-standard-support)
- [https://ubuntu.com/blog/ubuntu-18-04-eol-for-devices](https://ubuntu.com/blog/ubuntu-18-04-eol-for-devices)

ie. Ubuntu Pro & ESM only benefits you if using one of the 64-bit supported architectures; both 32-bits *architectures *are now EOL.

FYI:  I've still got an old IBM Thinkpad t43 running on a pentium M box using 18.04/*bionic*, mine will move to Debian like my other *i386* boxes already have..

---

### Post by Petr_Be on 2023-06-01
Thanks @1fallen, I changed the desktop icon from "spotify" to "firefox https://open.spotify.com" and I will see what the users' opinion will be :)

---

### Post by Petr_Be on 2023-06-01
Thanks @guiverc and wow, no! I can't believe I omitted this, I thought we would have an updated system for the next five years (if the HW will last that long which it wont;-) while in fact we were just receiving updates from the regular 18.04 release which is EOL today. I will consult what we will do. Perhaps migrating to Debian? You seem to suggest that Debian has an updated i386 release, I'll look into that.

---

### Post by ajgreeny on 2023-06-01
Don't forget that any 18.04 version of the *buntu family lost support a month ago, more or less, so you are running a huge risk if you continue to use your current 18.04 32bit Xubuntu.

You will be much better and more securely served using another distro, the most obvious suggestion being Debian with the Xfce desktop which will look remarkably like your Xubuntu and with a few exceptions works in the same way with the same commands, if you use the command line.

Give it a try! You can even use sudo exactly like you do in Xubuntu and do not have to worry about a separate root password if you choose that option when installing and choosing the username and password.

---

