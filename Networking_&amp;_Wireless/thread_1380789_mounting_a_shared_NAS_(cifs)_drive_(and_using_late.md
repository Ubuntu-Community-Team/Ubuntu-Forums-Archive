---
title: "mounting a shared NAS (cifs) drive (and using latex)"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by steple on 2010-01-14
I am encountering some weird problems when mounting a shared NAS drive (and using Latex (and subversion)).

First it was quite a hassle to mount the drive and have read write permissions as a user. I figured out that the probably correct way of doing it in /etc/fstab is:

```
//server/share /home/me/folder cifs user,noauto,username=#,password=#,domain=# 0 0
```[FONT=Courier New]user[/FONT] so that I can mount the drive as user and don't have to use sudo. (If I used sudo, all files would be owned by root and would not have read write access as a user.)

[FONT=Courier New]noauto[/FONT] because auto won't work since the network connection is not established when the mounting is done while booting.

So then I can do mount folder and voila everything works. I am listed as the owner of all files, although I am not, but I guess that is because the share is on a windows machine. I have access to the folders that I am supposed to have access to and everything works fine, except:

```
$ latex foo.tex
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
! I can't find file `foo.tex'.
<*> Please type another input file name:

```The file is definitely there though, e.g.

```
$ cat foo.tex | latex
```will work fine.

(Also, [FONT=Courier New]svnadmin create[/FONT] will not work. But this might be a problem with Berkeley DB, which is not supposed to be used on a shared drive.)

Any ideas what I might be doing wrong here?

---

### Post by jenast on 2010-03-26
I don't know of a solution, but I am also experiencing this problem with a cifs mounted network drive.

As for now, I have to work on a local disk when using latex, which breaks up my workflow pretty badly.

> texi2pdf foo.tex


Results in:

> 
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 file:line:error style messages enabled.
 %&-line parsing enabled.
entering extended mode
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, polish, swedish, loaded.
! I can't find file `./foo.tex'.
<*> ...3 \let~\normaltilde  \input ./foo.tex
     

I would also be interested in a solution.

---

### Post by kcho on 2010-06-01
I have the same problem here, no solution yet :(

---

### Post by rmbzz on 2010-06-13
I had similar problems and found that adding the options
nobrl and noserverino to the mount line fixed the problem.
Thus I am now using the follow mount command

```
sudo mount -t cifs -ousername=<server_user_name>,uid=<local_user_id>,gid=<local_group>,file_mode=0777,dir_mode=0777,nobrl,noserverino //server/path /mounts/localmountpoint
```
 

Visit
[http://tug.org/pipermail/tex-k/2010-June/002183.html]("http://tug.org/pipermail/tex-k/2010-June/002183.html")
and 
[http://www.tug.org/pipermail/tex-live/2010-March/025026.html]("http://www.tug.org/pipermail/tex-live/2010-March/025026.html")

The solution was given in the thread 

[http://www.openoffice.org/issues/show_bug.cgi?id=104974]("http://www.openoffice.org/issues/show_bug.cgi?id=104974")

Scroll down to the comments posted on
Mon Dec 14 07:46:55 +0000 2009

---

### Post by kcho on 2010-06-14
> **rmbzz said:**
> I had similar problems and found that adding the options
nobrl and noserverino to the mount line fixed the problem.

It works! thank you very much!!!!
:guitar:

---

### Post by DarkDead on 2012-12-09
Thanks rmbzz!

Adding nobrl and noserverino to the mount options solves my problem though just partially. If I generate a dvi, i.e. running ```
latex foo.tex
``` everything works fine. But if I try to generate a pdf, ```
latex -output-format=pdf foo.tex
``` or ```
pdflatex foo.tex
``` I get the following error:
```
!pdfTeX error: latex: getcwd() failed (No such file or directory), path too lon
g?
 ==> Fatal error occurred, no output PDF file produced!
```

As it says it's a getcwd() error which I can solve only by removing the noserverino, but then I get back into the
```
! I can't find file `foo.tex'.
```
error reported by steple.

Thus I'm in a loop. Any ideia to get me out of this?

---

