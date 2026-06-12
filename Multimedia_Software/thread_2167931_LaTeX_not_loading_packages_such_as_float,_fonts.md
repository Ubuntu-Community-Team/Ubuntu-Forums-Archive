---
title: "LaTeX not loading packages such as float, fonts"
date: 2013-08-15
forum: Multimedia Software
---

### Post by saraiwashere on 2013-08-15
Hello Ubuntu People,
I had an account on these forums but for some reason when I tried to use SSO for the first time entering my email took me to this account. I didn't even choose this username, I have no idea where it came from. This was my old account: [http://ubuntuforums.org/member.php?u=720166](http://ubuntuforums.org/member.php?u=720166). Anyway, I spent some time trying to fix it but I am not sure if I even really care.

Anyway, my main problem: I have been using Arch for a few years and moved back over to Ubuntu a couple of months ago. I am using 12.04 LTS because my computer didn't seem to support 12.10 ([read about it here]("http://ubuntuforums.org/showthread.php?t=2158654"), if you're curious). Everything seems to work well except I need to type up a couple of LaTeX documents and have had no luck. On Arch I used LaTeX as my main "word processor" and I used a base document with this code for typing up lab reports:
```
\documentclass[12pt]{report}
\usepackage[letterpaper]{geometry}
\usepackage{amsmath}
\usepackage{cmbright}
\usepackage{multicol}
\usepackage{float}
\geometry{tmargin=.5in,bmargin=.5in,lmargin=.5in,rmargin=.5in}
\setlength{\parskip}{\medskipamount}
\setlength{\parindent}{0pt}
\begin{document}


document test


\end{document}

```

I have always used pdflatex to compile the document into a pdf, which is typically what my professors like to get and is easiest for me to store and print. 

The first time I tried it with out of the box Ubuntu, I got an error about "cmbright.sty" being missing. I did some research and learned that my texlive package was hopelessly out of date (it was 2009) so used the instructions [here]("http://askubuntu.com/questions/163682/how-do-i-install-the-latest-tex-live-2012") using the backports ppa to get a new version of texlive. 

I can confirm by looking at my package list that I have the following packages installed: luatex, tex-common, tex-gyre, **texlive**, texlive-base, texlive-binaries, texlive-common, texlive-doc-base, texlive-extra-utils, texlive-font-utils, **texlive-fonts-recommended**, texlive-fonts-recommended-doc, texlive-generic-recommended, texlive-latex-base, texlive-latex-base-doc, **texlive-latex-extra**, texlive-latex-extra-doc, **texlive-latex-recommended**, texlive-latex-recommended-doc, texlive-luatex, texlive-pictures, texlive-pictures-doc, texlive-pstricks, texlive-pstricks-docs. (emphasis mine)

However, I am having the same problem still. The latex output confirms that I am now using the correct 2012 edition of texlive. I cannot find any more information or solutions to this because it seems to have been fixed for everyone else by updating to 2012 texlive. Here is the full error output: [http://pastebin.com/n2iuz2hq](http://pastebin.com/n2iuz2hq)

[s]If I remove cmbright as a package, it simply gives the same error with float instead.[/s] The default font is hideous and I cannot properly float my tables for lab results without the float package. Hopefully someone has a solution to this! Nothing else has the same math support as latex and I really need it.

Thanks!!

[UPDATE: My apologies, I tried it again and it seems that with the new updated 2012 texlive FLOAT does work. Not cmbright, though.]

---

### Post by Irihapeti on 2013-08-15
To get your old forums account back, post in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123") and an admin can help you.

---

### Post by saraiwashere on 2013-08-15
Thank you, I have posted there.

Ok, update on the main problem.

Since float works, I figured there's nothing major wrong with my texlive install and so I might just be able to download and install cmbright separately. I used this download and installed it without issue and ran texhash to update the package cache.

However, it seems that that package does not contain scalable fonts and so it ends up looking like this: 
[[IMG]http://s10.postimg.org/4qaui1rb9/Screenshot_from_2013_08_15_15_30_23.jpg[/IMG]]("http://postimg.org/image/4qaui1rb9/")
(the bottom one was compiled on my old arch linux install, the top one with the new cmbright font- same exact .tex document)

I have not been able to find any scalable version of cmbright though obviously it exists because I used it before** because it came preloaded on my old install**.

So needless to say I'm frustrated but hoping someone can help me?

---

### Post by GwL3eNC on 2013-08-16
Hi,

i have also used latex during my study and loved it. I do it with eclipse and the lexlipse plugin. It works
realy well. your errors tell about a missing sty file

 LaTeX Error: File `cmbright.sty' not found. 

I think you  must  download [http://www.ctan.org/tex-archive/fonts/cmbright](http://www.ctan.org/tex-archive/fonts/cmbright) and install that (sorry now i have seen you already done that, but in another way). I install packages with tlmgr, no texhash is needed.

tlmgr install <package name>

Whish it takes you further.

[http://www.tug.org/texlive/doc/tlmgr.html](http://www.tug.org/texlive/doc/tlmgr.html)

PS: I prefer to install texlive complete, but if you dont change the donwload mirror (see install instructions [http://www.tug.org/texlive/quickinstall.html](http://www.tug.org/texlive/quickinstall.html)) it takes
very long time. I use this mirroe instead [http://ftp.uni-erlangen.de/mirrors/CTAN/systems/texlive/tlnet/](http://ftp.uni-erlangen.de/mirrors/CTAN/systems/texlive/tlnet/)

---

### Post by Sarai the Geek on 2013-08-16
Something must be wrong with my texlive install after all as, I don't seem to have the tlmgr utility:

```
sarai@sarai-laptop:~$ tlmgr install cmbright
No command 'tlmgr' found, did you mean:
 Command 'vlmgr' from package 'qdbm-util' (universe)
 Command 'rlmgr' from package 'qdbm-util' (universe)
tlmgr: command not found

```

I will try to uninstall my version of texlive completely and install according to the instructions you posted.

[EDIT: oh and in case it wasn't immediately obvious, I did recover my account. Thanks, Irihapeti]

---

### Post by GwL3eNC on 2013-08-16
I dont know, but possibly if you choose texlive from the ubuntu build in sources it's an old version without 
tlmgr. I would also completely remove this old installation and then donwload the install script from above.
I would be happy if the new complete installation solve your problem.

---

### Post by Sarai the Geek on 2013-08-16
Well, the download just finished (82 minutes!) and it is downloading now so hopefully I will know soon?

---

### Post by Sarai the Geek on 2013-08-16
So, it downloaded and installed with no problem. I tried to follow the instruction to edit PATH (which is a function I am wholly unfamiliar with and doesn't seem to be well explained anywhere) by putting a script called texlive.sh with the path in /etc/profile.d/ and giving it executable permissions.

The long and short of it is now my computer is completely broken. I get to the login prompt and when I type in my password it acts as if it is logging in and then boots me back to the prompt. I know I am entering the correct password because if I try anything else, it says "incorrect password". The same thing happens when I attempt to log in as a guest.

I couldn't find my Ubuntu boot disk anywhere so I am having to download and burn another one. However, historically my computer has not done well with boot disks- there is something wrong somewhere in the hardware and it took the computer technician several tries to install Ubuntu in the first place (I had to PAY someone to do this because it was the middle of the semester and I had no time to do it myself), he eventually succeeded using a thumb drive of Ubuntu LTS. I may have to reinstall and I'd be lucky if I could get that to work.

So to sum up, because I hated the way a bitmap font looked in latex, I have quite possibly irreparably broken my computer.

---

### Post by GwL3eNC on 2013-08-17
Hello,

that dont sound good, but  i'm absolutly shure that the texlive installation dont kill your system. It never happend
to me. Because i use an Editor i must never set a path, in the preferences of my editor i set this. However, i dont
think your script or the installation is the problem.

The problem you tell about (login loop) can happen if some files of your X System are missing, removed or broken.
If this problem would happen to me (i use kubuntu) i would complete reinstall my Desktop environment. Can you login
over terminal (for example on grapphical login type STRG+ALT+F1 to get konsole login)? If this works you can
try reinstallation. Which KDE do you use?

Because of the caption of your thread some people dont look at it. Also it's in Multimedia section. If we can't solve
your looping problem you can open a new thread about it and place it to a better categorie. I'm shure this
is well known.

---

### Post by Sarai the Geek on 2013-08-18
Ok, that is a good idea. I will open a new thread.

---

### Post by Sarai the Geek on 2013-09-10
At long last, this is solved. Since my old computer failed, I got a new one which can run Ubuntu 13.04. 13.04 repos contain the latest-greatest version of texlive and a vector font of cmbright.
So, it now does what it should. The solution to this problem is to upgrade to 13.04.

I can't mark this as solved, because I made the thread under a different username, though. :(

---

