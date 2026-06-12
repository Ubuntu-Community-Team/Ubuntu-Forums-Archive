---
title: "ISO troubles"
date: 2009-01-20
forum: Mythbuntu
---

### Post by csbright on 2009-01-20
okay, i have found myself laid up in bed after a spinal surgery. so please bare with me as i try to explain what i am trying to do.

Okay so here goes, one of my projects is to convert all the dvd's i own into ISO's i can store on a server. i have decided to use iso because i want to store the dvd basically uncompressed and intact. i know this can be done other ways but... this was my option. so i use a piece of software to create the iso's called Any DVDHD. and then mount the iso using a virtual drive to watch each iso via powerdvd or VLC. so here is my issue. So right now if i want to watch a movie i right click on virtual choose mount... find the iso mount it abd then choose play with vlc media player.   now what i am looking for a some sort of way via "mythbuntu" of being able to when doing a search of MEDIA ON MY DRIVES. Im curious if there was anyway or any program that would read each iso find the table of Content and add each movie into a searchable database with coverart etc etc just like it might any music you have stored on your drives.    God I hope this all makes sense. Or am i barking up the wrong tree????

---

### Post by csbright on 2009-01-21
hey guys if i am barking up the wrong tre with my question. please let my know and i will look for a different program/OS  it was a buddy of mine that pointed me to mythbuntu and he was sure you could help me out in pointing me in the right direction. 

if not.. thanks much to the 7 people that at least read my post.

---

### Post by larsolav on 2009-01-21
Hi. Wish you a speedy recovery!

I basically have all my kids DVDs in ISO format on my Mythbox. I have the ISOs in the mythtv videos folder, but you could also put them on a remote server and access them from your mythtv frontend.

Mythtv can look up your ISO file on IMDB and import the poster and other information, but the file name of the ISO has to be identical to the movie tittle, otherwise it is easy to find the IMDB number and insert that in a search too.

The internal player in Mythtv may have a problem playing certain ISOs, but you could tell myth to use Xine to play your ISOs instead. (see my post at [http://ubuntuforums.org/showthread.php?t=951590]("http://ubuntuforums.org/showthread.php?t=951590") )

Is this close to answer your question?

---

### Post by csbright on 2009-01-22
Hey thanks, I think this might work. I am stil yet to get this all up and running and I am affraid that I am a total novice at this and will be looking for maybe some serious support. I want to store all the movies on a seperate server etc etc. I hope no one is going to mind my total noviceness....  I will have questions like should I run a seperate SQL server machine. Should I have my files all stored on the same machine as the SQl server. Should I leave the SQl server on the same machine as mythbuntu...  And would someone be willing to point me in the direction of the Mythbuntu for Idiots instruction book :-). 

I am really excited to get this running.  

On another note I have been looking for a great tv tuner card/digital AST tuner. i do not want to steal digital or hd tv but want it to work flawlessly with comcast. If does not have the ability to record hd, only starndard broadcast i will be happy as well. But i am looking at wanting to record uncompressed. i am not so worried about the hard drive space.  As i a sure you can all tell i am a total noob!!!!!!!!  

Seriously would i just be smarter to purchase the prebuilt machine you offer?

much much much thanks to anyone who reads and responds to this i will owe someone :D

---

### Post by Archmage on 2009-01-22
I think it makes sense to have the MSQL-Database and the ISO-Files on the same server. I have them on my primary MythTV-Backend and on every PC that I have MythTV-Frontend installed I can watch and update the database.

Two remarks: You need to allow connections from outside to the MSQL-Database (one setting in MythTV) and the files should be on a folder that is shared and everywhere identical named. I'm doing this via NFS.

---

