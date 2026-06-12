---
title: "Help Updating CUPS To 1.2 Or Higher / Installing Lexmark X2600 Series"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by DetectorX on 2009-08-28
Hello and thanks for the help in advance...

I made a complete migration to Ubuntu a few months ago, three production desktops, one netbook and one play machine. I must say I'm impressed. There is absolutely no way anyone could talk me into going back! With that said Ill quit rambling and get right to the point.

Since the migration I have overcome many hurdles and amazingly enough feel that things a running much smoother and much more efficient overall, for the most part. There is only one hurdle I have yet to overcome, That is successfully installing a Lexmark all in one "X2600 series" on any of my machines running 9.04.

Now I am desprate, I need to at the very least get one of the two, both basically the same models, to print! I have searched high and low, tried different tutorials, nothing has worked thus far.

Lexmark has installer package on their site for which I believe are basically for Ubuntu "Debian based", the installer starts up runs then throws up a CUPS error, needs CUPS 1.2 or higher. So I search and search for another resolution and I find a few solutions, though I cant get them to work, this hack seems to be the best option "http://ubuntuforums.org/showthread.php?p=7713382#post7713382". Though once unzipped I end up with one file "lexmark-inkjet-08-driver-1.0-1.i386.deb.sh." Nothing that I can open with a text editor and modify.

Is there a simple way to update to cups 1.2? If so would you be kind enough to walk me through it? Money is tight I live from job to job and affiliate check to affiliate check, so I really dont want to have to buy something new, even though it's only about 70 bucks.

If there is really no reasonable solution to installing this Lexmark X2670 "X2600 Series," I guess Ill have no other choice but to buy something different. If this is the ultimate answer which brand and model / models would be my best choice /choices?

Machine running Ubuntu 9.04,
installing Lexmark X2670 "X2600 Series"
Cups Version 1.1.3 "Almost sure"

Thanks again, dX

---

### Post by nathan726 on 2009-12-01
You do not need to update cups. Cups is fine. The actual problem is the script that Lexmark use to check your cups version... it doesn't work correctly. The only way to install the driver is to fix the script as discussed in detail [here]("http://ubuntuforums.org/showthread.php?t=1223710").

When you extract the .zip file you get a .sh file and then you need to dump the contents of that file, to access the files inside by running this code:

```
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh --noexec --target lexmark_install
```

---

