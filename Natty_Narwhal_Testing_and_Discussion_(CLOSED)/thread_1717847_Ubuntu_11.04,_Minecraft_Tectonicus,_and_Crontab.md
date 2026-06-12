---
title: "Ubuntu 11.04, Minecraft Tectonicus, and Crontab"
date: 2011-03-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Rikeshar on 2011-03-30
Hello everyone, I'm hoping you can give me some help figuring out what might be going wrong here. 

I'm running Ubuntu, and have created a script which will automatically fetch a file from the server I'm running Minecraft from. There is then a java program called Tectonicus which uses the data in the world folder to generate a Google-maps style map of the world. The script I've written is:

```

/usr/bin/scp -r USERNAME@SERVER:/home/zach0242/minecraft/world /home/thornbury/Desktop 

java -jar /usr/games/Tectonicus_v1.30.jar worldDir=/home/thornbury/Desktop/world outputDir=/home/thornbury/Desktop/TectonicusTest cameraAngle=225 imageFormat=jpg minecraftjar=/home/thornbury/.minecraft/bin/minecraft.jar playersInitiallyVisible=false signs=all signsInitiallyVisible=false useBiomeColours=true 

rm -rf /home/thornbury/Desktop/world

```...where "USERNAME" and "SERVER" have their appropriate values. 

I have this script, titled tectonicus, on my desktop. If I run the script from the command line:

```

/home/thornbury/Desktop/tectonicus

```... it runs perfectly. The trouble I"m having is that I"m trying to create a crontab to run it remotely. The crontab looks like:

```

30 12 * * * /home/thornbury/Desktop/tectonicus

```... and I've been changing the timing to test.

What's going on is that the script will execute, the world file is downloaded and Tectonicus starts... but it doesn't finish. It creates the TectonicusTest file on my desktop, creates the Cache folder with the skineCache, tileCache, and tileLists folders, which are empty. After this it deletes the world folder from my desktop and that's it. I tried removing the line that deletes the world folder from the script, and the only difference it made was that the folder wasn't deleted; Tectonicus still didn't finish running after only making those files.

I tried running the crontab with crontab -e and sudo crontab -e, thinking there might be a permissions conflict, to no avail. 

Any ideas?

---

### Post by uRock on 2011-03-30
Please create Natty threads in the proper sub-forum as it is still in the testing/development stage.

Moved to NNT&D.

---

### Post by Rikeshar on 2011-03-30
Okay, thanks. I wasn't sure if it was a Natty problem specifically or not, which is why I left it in general.

---

### Post by cariboo on 2011-03-30
I doubt if it really is a problem specific to Natty

---

### Post by Rikeshar on 2011-03-30
It wasn't. Needed a DISPLAY in the crontab to get it working

---

