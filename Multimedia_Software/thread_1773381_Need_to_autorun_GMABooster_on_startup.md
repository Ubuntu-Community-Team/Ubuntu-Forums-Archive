---
title: "Need to autorun GMABooster on startup"
date: 2011-06-02
forum: Multimedia Software
---

### Post by lkh1966 on 2011-06-02
Hi,

Pls pardon me if I have posted on the wrong section.

My system -

- Win-XP Home netbook with Wubi-Ubuntu 10.04 Desktop
- GMABooster utility for Ubuntu

To use GMABooster, I would "sudo path/to/./GMABooster 400" in Terminal.
Afterwards, "sudo path/to/./GMABooster --detect" would confirm the settings.

I wish to autorun this utility on startup. So I wrote a shell script to try out -

_GMABooster.txt_
#400MHz
sudo ./GMABooster 400

When I ran the txt file in Terminal, GMABooster failed to launch.

For a start, pls correct my script.

I'm new to Ubuntu & needs lots of guidance. TIA.

---

### Post by webofunni on 2011-06-02
I am not able to see your script. Please attach it or put that in code tag.

---

### Post by lkh1966 on 2011-06-02
> **webofunni said:**
> I am not able to see your script. Please attach it or put that in code tag.

_GMABooster.txt_
#400MHz
sudo ./GMABooster 400

Above refers to the name of my script file & the 2 lines of text in the file. Hope this is clear to all.

---

### Post by webofunni on 2011-06-02
Thanks, But that was confusing. It always good to give proper extension for the files. Shell scripts usually end with .sh. 

Now, how you are executing the file. If you are just doing ./filename, then it is always good to add the #! line. 

say #!/bin/bash

also where is that GMABooster located, is that in the same folder where the script resides ?. I suggest to give full path. 

sudo /whatever/..../GMABooster

What is the exact error you are getting ?

---

### Post by lkh1966 on 2011-06-03
Let me try to simplify things further.

I have a folder called GMABooster with an .exe file of the same name. The file path is like this -
/home/(user)/Documents/GMABooster/GMABooster.exe.

From here, how do I write a shell script to launch the utility? (refer to my 1st post on the Terminal commands)

In which folder should I put this script file?

Specifically, what texts should be written in the shell script?

---

### Post by webofunni on 2011-06-04
> **lkh1966 said:**
> Let me try to simplify things further.

I have a folder called GMABooster with an .exe file of the same name. The file path is like this -
/home/(user)/Documents/GMABooster/GMABooster.exe.

From here, how do I write a shell script to launch the utility? (refer to my 1st post on the Terminal commands)

Why you are trying to execute an exe, I can see they are providing a linux version of same utility. You need a package called wine to execute exe in linux. But I am not sure, if this exe file is compatible with wine. 

> 

In which folder should I put this script file?

Specifically, what texts should be written in the shell script?


You can put the script anywhere, but you need to change the file path specified in the script accordingly.  You can just put what ever you are executing in terminal. But keep an eye on the file path. 

Bt, what exactly you are executing in terminal and what is the output you are getting ?

---

### Post by lkh1966 on 2011-06-04
Maybe it wasn't clear to you in my 1st post.

I'm already using the linux version of GMABooster (no need for WINE). BTW, it's for overclocking Intel GMA945 chip to a max of 400MHz.

I have no problem launching it in Terminal (again refer to my 1st post on the commands).

What I'm hoping to achieve is to autorun this utility each time I boot into Ubuntu instead of having to activate overclocking manually.

---

### Post by lkh1966 on 2011-06-05
Thks Webofunni for your responses. But I finally got it figured out.

What I did is to add a new item to System - Preferences - Startup Applications. In the Command box, I typed in"gksu path/to/./GMABooster 400".

Now each time I startup Ubuntu, I'll be prompted for my password & bingo, the overclocking utility will kick in.

---

