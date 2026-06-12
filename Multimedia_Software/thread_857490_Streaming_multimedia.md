---
title: "Streaming multimedia"
date: 2008-07-12
forum: Multimedia Software
---

### Post by jiggygent on 2008-07-12
Hello all, 

I would like to setup my Ubuntu desktop edition to stream video/audio to other devices.. ie Wii or other computer via web browser. I've been researching and have heard of installing LAMP and Jinzora.  This seems to be a complicated setup, but was hoping for a howto.  Does anyone have a link or instructions on how to setup both?  I found [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) , but that's just for LAMP setup and I plan on setting this up specifically for Jinzora so not sure if that applies or not.  Any help would be greatly appreciated.  Thanks in advance!

---

### Post by jiggygent on 2008-07-12
Does anyone have this setup that can help??

---

### Post by steve8track on 2008-07-12
I've set up jinzora before, but it's been a while.  You need php and mysql setup, then you just download jinzora, extract it to your webspace, and browse to it in your browser.  It will take you through the setup process.  Afterword, make sure to do what it says with the installation scripts (delete or move them out of the webspace) so that others can't re-run the setup process and change the settings, etc.

I hope this helps,

Steve

---

### Post by jiggygent on 2008-07-13
I'm not sure I understand exactly.. I installed php, sql and apache.. I downloaded and extracted jinzora to my desktop.  I reviewed the install.txt file in the jinzora2 folder.  It says to open index.php in my browser.. Not sure what browser it means.. I can open it in a text editor, but not in firefox.  I'm assuming by browser it means web browser right?  I feel like such a noob.. But I hope it's not opening the index.php in a txt editor because it just all looks like greek to me in there.. :confused:

---

### Post by cariboo on 2008-07-13
To get jinzora you have to copy the jinzora driectory and files  to /var/www, which is your apache2 document root directory. If you have a look at:

[http://freshmeat.net/](http://freshmeat.net/)

and search for mp3 servers you will find several more choices.

JIm

---

### Post by jiggygent on 2008-07-13
OK, so I copied the jinzora2 directory to var/www..  I'm not trying to setup an mp3 server, I would like to stream movies.. So now it's in the /var/www directory.. But it still executes in a txt editor or if I try a web browser, it wont work..

---

### Post by jiggygent on 2008-07-17
hmm.. I guess I'll have to give this project up.  There is hardly any documentation on how to setup Jinzora and apparently, not too many Ubuntu users have experience with it.  I guess as an alternative I will setup a Samba share and just use my xbox running XBMC to access my movies/music..  On to the next project!  Thank you anyways for the assistance.

---

### Post by Lul2x on 2008-10-09
I know I'm bringing up an old post, but there is a nice tutorial for this here: [http://rubbervir.us/projects/ubuntu_media_server/part2.html](http://rubbervir.us/projects/ubuntu_media_server/part2.html)

---

