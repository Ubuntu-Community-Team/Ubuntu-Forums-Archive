---
title: "[SOLVED] RockBox Utilitie install question."
date: 2008-08-27
forum: Multimedia Software
---

### Post by LowMen on 2008-08-27
I have been using Vbox as a buffer as I learn to use Ubuntu.  I downloaded the Rockbox Utility for Linux, right clicked and extracted to the desktop. 

The file downloaded as "rbutilqt-v1.0.6.tar.bz2" and now there is a folder that has a file named "rbutilqt-v1.0.6" on my desktop. In the mentioned folder there is a file named "rbutilqt"  If I double click the file it does load Rockbox utility. I will ask my question as if I were in windows and hope you can understand and translate to Linux speak basically.

I would like to know if I can run a command that would file this program either into a list where I can click on applications and choose a folder in said dropdown and then click on rockbox, instead of opening up a file on my desktop and then clicking the "rbutilqt" file. 

Thank you, hopefully I did not turn a simple request in my mind into goop for you to read.

LowMen

---

### Post by joris1977 on 2008-09-25
Thanks for your post. I was struggling to get Rockbox Utility running and for some reason i didn't even think of just clicking on the rbutilqt file. The most obvious stuff seems to cause trouble for me... ;)

Well maybe i can help you with your question. If i understand it right you want to make a launcher under the Applications menu. That is pretty easy. Move the 'rbutilqt-v1.0.6' folder to your home folder. To keep your home folder organized you might want to rename it to .rbutilqt-v1.0.6. So it will be a hidden file. You can still see hidden files in Nautilus, the file browser, under view -> show hidden files. 

Right click on the applications menu and choose edit menus.  Now a screen opens with on the left side Menus and on the other side Items. You probably want to File Rockbox under Sound and video, so click on Sound and videos under Menu. Now you see all the items in the Sound and video menu. 

Click on the button with '+ New Item' Now opens a pop-up that says create new launcher.  Type should be Application.  Give it a Name under Name most likely something like Rockbox Utility. Most important is the command. There is a button and you can browse to the rbutilqt file in your home folder. Click on the file and the command will be /home/yourname/.rbutilqt-v1.0.6/rbutilqt

You can press Ok now and than you have a launcher in your menu, but wait because probably you want to have a nice picture and not the strange default gnome-applications icon. You can use any icon for this. It should have a width of 64 pixels and a height of 64 pixels. I don't know for sure, but i guess it should have a .png or .svg extension.  Store the icon somewhere in your home folder. I did put it under Pictures. On the Create Launcher pop up you can right click on the icon and browse to the place where you stored your icon.

Click Ok and that' s it now you have a nice launcher on the menu.  

It took me some time to find a nice icon, you can save yourself that time and download mine -> [http://i473.photobucket.com/albums/rr100/wijdehei/rbutils.png](http://i473.photobucket.com/albums/rr100/wijdehei/rbutils.png)

---

### Post by LowMen on 2008-10-02
Thank you very much for the reply, I will have to change that icon to a .svg later but you saved me lots of time.  Also please excuse my long delay in replying back, I have been very busy latly.  

Your instructions above worked like a charm :)

---

