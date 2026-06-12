---
title: "K3b problems"
date: 2009-07-11
forum: Multimedia Software
---

### Post by jmfal on 2009-07-11
Hi, everybody, new to ubuntu so be patient with me.
When I, start up k3b it shows up on screen then after 30sec disappears,then window pops up>error:malformed URL file://home/myname< then when I close that I get another window> could not find mime type application/octet-stream
I`ve tried reinstalling in both add/remove and synaptic, same errors.

---

### Post by HappyFeet on 2009-07-11
Go to your home folder and do Ctrl-h. That will show you the hidden folders. Delete the .kde folder and restart K3B. Let us know what happens.

---

### Post by d_liebscher on 2009-07-11
Hi,

try to rename “octet-stream.desktop „  in: ~/.kde/share/mimelnk/application to octet-stream.desktop.bak

deleting the whole directory .kde should have the same effect, but it is a bit excessiv ;)

Daniel

---

### Post by jmfal on 2009-07-11
re:happyfeet
opened home folder>ctrl-h< nothing
tried opening files in home >ctrl-h< nothing
tried opening kdesomething >ctrl-h< nothing
maybe i`m doing it wrong?

re:d_liebscher
opened abunch of folders in home can`t find it,if it can be found from a terminal,i`ll try that, remember i`m noobie

---

### Post by d_liebscher on 2009-07-11
Hi,

this files are hidden, and the shortcut Ctrl+h is to show hidden files, but it depends on the Filemanager (in Dolphin it is Alt+.
View-> Show hidden files should have the same effect.

to rename a file from console, you can use:

```
mv ~/.kde/share/mimelnk/application/octet-stream.desktop ~/.kde/share/mimelnk/application/octet-stream.desktop.bak
```

---

### Post by jmfal on 2009-07-11
re:d_liebscher
in the terminal entered
mv ~/.kde/share/mimelnk/application/octet-stream.desktop ~/.kde/share/
mimelnk/application/octet-stream.desktop.bak
terminal says command not found,I don`t think the complete command fit in the window in your reply thanks

---

### Post by d_liebscher on 2009-07-11
hi,

hm, could by also an typing error.

let's try it step by step

1 change the directory to this file

```
cd ~/.kde/share/mimelnk/application
```2. look, if this file exists
```
ls | grep desktop
```if it is listed:
3a. rename the file
```
sudo mv ./octet-stream.desktop ./octet-stream.desktop.bak
```if it is not listet (HappyFeet was right than, and I was overcautious ;) ):
3b. go back to home directory and rename .kde folder to .kde.bak
```

cd ~
sudo mv ./.kde ./.kde.bak

```Daniel

---

### Post by jmfal on 2009-07-11
re:d_l
replies from terminal
#1:no such file or directory
#2: examples.desktop
#3a: no such file or directory
#3b:no such file or directory
???? I remember having some problems w/my internet connection about a month ago during a update/download maybe thats why nothings there. I`v been working alot and really haven`t had time to go through everything and see if all of it is working. thanks. throw some more at me, I want to get this working, i tried brasero i don`t want to mess with it.

---

### Post by d_liebscher on 2009-07-12
hi,

ok

one terminal command:

```
sudo mv ~/.kde ~/.kdeold
```I tested it, and it work on every linux system, where kde applications run. If the result is something like "no such file or directory" there are other problems, which I can't figure out his formulation of problem.


Daniel

---

### Post by jmfal on 2009-07-12
re:D_Liebscher
Good morning, entered command in terminal, asked for password nothing came up, just waiting for next command.
entered same command, this time eliminated spaces>no command found
Is there something missing from kde in repos that needs to be installed?
Keep them coming ,and i`ll try it. THANKS

---

### Post by d_liebscher on 2009-07-12
hi,

after you run this command k3b should work without problem.

Daniel

---

### Post by jmfal on 2009-07-12
re:D_Liebscher
Tried command again, just came back waiting for next command, tried to open k3b and have same error windows.

---

### Post by d_liebscher on 2009-07-12
hi,

at first:
it is really not easy to find out, what's going on on your system, because i just know just some simple facts about it

I summarize now what I thought (if some facts here should be wrong, please tell me):

1. you have 2 problems
   a - Mime types
   b - error:malformed URL file://home

2. problem a (Mime types) is not so problematic
    in my opinion the reason is using a kde application on Gnome
    solution is to add a line in some files but k3b should also run without it (just error message)
    same problem is discribed here: [http://ubuntuforums.org/showthread.php?t=192284](http://ubuntuforums.org/showthread.php?t=192284)
    (with solution, if you don't know how to add this lines, i'll explain it )

3. error b (malformed...) in my opinion the reason for k3b crash
    reason could be an distribution upgrade from GUI
    renaming the .kde folder (which you have done and which worked) should solve this, but it worked probably not 

4. how solve problem b
    after 3rd did not work apparently, please let us know what happen if you enter in a terminal:
```
k3b &
```and also what happen if you enter
```
sudo k3b &
```You said > I`ve tried reinstalling in both add/remove and synaptic, same errors.did you removed k3b with the option "completely" in synaptic? [if not, you should try reinstalling with this uninstall option at first of all]

Daniel

---

### Post by jmfal on 2009-07-12
re:D_Liebscher
I`ll make it quick, just got called to work today.
#1: yes
#2: tried command from jonrkc;; bash:no such file or directory
                      bash:octet-stream :no command found
#3: I don`t know, probably
#4: entered>k3b &
[1]6427 then said kbuildsycoca running...crashing, I dont have time to type it all in, then lists my dvd specs about 26 lines of it,then says something about dcopserver already running.I`m going to leave terminal open so i dont lose that info, if i knew how to paste terminal to reply i will.
last question..in synaptic i marked for removal,not complete removal, i was afraid that i would completly remove it from repos>noobie<
i`ll be back tonight to figure this out, thanks for your help!

---

### Post by d_liebscher on 2009-07-12
Hi, 

to copy terminal output, mark lines with mouse -> right click -> copy

Complete removal means that the configuration files are removed too, which is important in this case.

Daniel

PS: your tonight is very very early morning here, i would look tomorrow after work ;)

---

### Post by jmfal on 2009-07-13
re:D_Liebscher
Hi, did complete removal of k3b, install from repos, same error windows.

---

