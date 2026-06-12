---
title: "HOWTO: Getting rid of Amazon hurl.exe problems"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by adam_kimber on 2007-07-14
I came this problem the following problem this morning: 
Upon clicking on a media sample on Amazon when using Firefox I got the following pop up: 

**"hurl.exe File type Windows Executable"** and then a list of what to do with it, save etc. 

_Here is the solution (that worked for me)_

1) Grab the latest Realplayer from [here ]("http://www.real.com/linux") 

2) Then make the file executable, seeing as this will require installing from the command line i suggest the following method for installation

```

$ chmod +x RealPlayer10GOLD.bin
$ sudo ./RealPlayer10GOLD.bin

```

3) Then follow the instructions. I have used sudo so that I could install it within the filesystem so all users can use the program. However you can put it your /home directory if you want. 

Note: Make sure Firefox is closed for the installation in case the plugins do not get installed .

4) Once installed open Firefox, go to Amazon and click on one the Realplayer links that was producing the hurl.exe problem. 

5) Click on the open with drop down and select other. Browse to where you installed the program and select  "realplay" 

6) A dialog will pop up about the EULA and other things. Click next :) 

7) This should open the audio sample. If it does you can go back to Firefox and open the link again and select always do this option. No more popups, Realplayer will open and play the links

I hope this helps. Any suggestions for making this HOWTO better please post!

Adam

---

