---
title: "Runescape issue with sound and java  solved on ubuntu 11.04"
date: 2011-06-29
forum: Multimedia Software
---

### Post by gylti on 2011-06-29
Well this is amazing, after 4 months and just after I posted on here I have cracked it. 

This is on 11.04 Natty Ubuntu 

I have already switched to the Classic view in System then login 

Already I have installed 

GNOME Alsa mixer 

Pulse Audio 

Latest java mine is jre-6u26-linux-x64.bin installed via terminal into usr/local with symbolic link to Mozilla plugins and have removed icedtea symbolic link, instructions are on the java page where you download the .bin file 

removed the hot thingy java cant remember what it was called exactly, I removed with update manager 

if you put "about : plugins" into address bar of firefox you see what you have 

I have gone through so much and even lost all my loyalty points with this and even bought a new comp and sound card but here is the solution to getting all the sound in Runescape: 

***Check that nothing is muted in the GNOME Alsa mixer 

(and I just kept trying different combinations of this and the sound preferences until I had music playing - I mean any music - I played lots of Muse till I heard it.) I haven't got speakers on this comp only headset, may be shouting for quite a while now. 

***Once you know that you have sound, use SYNAPTIC and find the alsa-oss and alsaplayer-oss and install them. 
[B][U]
I now have MUSIC on my comp, MUSIC on Runescape and also SOUND EFFECTS on Ubuntu 11.04 You have to find the alsa-oss compatibility installations to make oss play through alsa player its that simple [/U][/B]


I REPEAT Once you know that you have sound on your computer, USE SYNAPTIC - find in synaptic and install these 2 packages 

alsa-oss 

and  
 alsaplayer-oss  
 

 Remove with package manager the other java versions except for icedtea (some other programs use this) 

Then using firefox go to the java site and test java - it should not work, if it does you have to remove the symbolic links in mozilla. 

Find the mozilla plugins folder in /usr/lib/mozilla 
and remove the link to iced tea and to any other java versions 
you can do this in terminal 
(all the instructions are on the java page) 


then you can download the latest java for linux from that same place as a .bin file and all the instructions are on the page as well as instructions for removing symbolic links using terminal. 
(put the file into /usr/local to install it) 


Only mistake in instructions on the official java page is that the symbolic link plugin ( li -s) has to go into the folder /usr/lib/mozilla/plugins 
NOT firefox/plugins 

Iced tea doesn't work anywhere near as well as the latest official java from their site. 

Make sure your graphics driver is installed (Administration additional drivers) 

Install using the software center the Gmome Alsa Mixer if you are on a gnome linux and also get Pulse Audio and Alsa Player then make sure your sound is ok on your computer, you may have to mess around with settings. 

Then install those 2 files and your sound should work as well

---

