---
title: "Installation of Java Media Frameworks fails"
date: 2008-08-04
forum: Multimedia Software
---

### Post by Bodolf on 2008-08-04
Rather new to Linux, I want to play videos in Openoffice Impress. I have followed the advice of james_h in
[http://www.oooforum.org/forum/viewtopic.phtml?t=26704&highlight=jmf](http://www.oooforum.org/forum/viewtopic.phtml?t=26704&highlight=jmf)
and the installation in the terminal works passed the three questions, where I answer yes-no-no as adviced. Then I get the following message in the terminal:
----------------
Unpacking...
tail: cannot open `+309' for reading: No such file or directory
Extracting...
./install.sfx.11277: 1: cannot open ==: No such file
./install.sfx.11277: 1: ==: not found
./install.sfx.11277: 3: Syntax error: ")" unexpected
chmod: cannot access `JMF-2.1.1e/bin/jmstudio': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfregistry': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfinit': No such file or directory
./jmf-2_1_1e-linux-i586.bin: 305: JMF-2.1.1e/bin/jmfinit: not found
/bin/cp: cannot stat `JMF-2.1.1e/lib/jmf.properties': No such file or directory
Done.
----------------
I have observed that the size of the jmf-2_1_1e-linux-i586.bin file is 2.3 MB prior to trying to install, afterwards it's 0 B. I have tried it twice with the same result.
Can anyone help me out here, please?

---

### Post by mauri23 on 2008-08-08
Hi Bodolf!
First excuse me for my english...

I've had the same problem, and after two days I resolved it.
The reason of the crash is a different syntax for the command "tail" used in the installation script, which is relative to another linux distribution (I don' remember which one...)
So the solution is very easy: since the script only extract the files contained in the bin file, you can open the bin file in Win OS with WinRar, extract the files, e copy these files in ubuntu...and all works fine. 
:)

---

### Post by Bodolf on 2008-08-17
Thank you for your advice! The actual problem has been showing video in Openoffice Impress. I though JMF was the key to smooth video presentations, but I have now understood that, in Ubuntu, Gstreamer takes care of it... presentations with video won't import video functionality from PowerPoint, and when I insert video in a new Impress presentation the slide only shows a big "?" in editing mode. The video will play in presentation mode, but only after a delay when a white box covers the slide, very irritating. By looking at different forums I understand that video support in Impress is not very good. This is too bad, and may be the dealbraker that forces me back to Windows. PowerPoint has its downsides, but playing video is not one of them, that is very well supported indeed.

Best regards
Bodolf

---

### Post by jtappin on 2008-09-25
> **mauri23 said:**
> Hi Bodolf!

So the solution is very easy: since the script only extract the files contained in the bin file, you can open the bin file in Win OS with WinRar, extract the files, e copy these files in ubuntu...and all works fine. 
:)

Not so easy if you don't have windows. 

The proper fix is to edit (with due care and attention as parts of the file are binary) and replace
```
tail +305
```
with
```
tail -n +305
```
then it installs, however I'm not sure how useful it is since although jmfinit runs, jmstudio fails (at least with java 1.5.0) 

[I]Note added 13 Oct:

Turns out jmstudio works with java 1.6.0.
[/I]

Does anyone know whether Sun are even still supporting this as the files are several years old?

---

