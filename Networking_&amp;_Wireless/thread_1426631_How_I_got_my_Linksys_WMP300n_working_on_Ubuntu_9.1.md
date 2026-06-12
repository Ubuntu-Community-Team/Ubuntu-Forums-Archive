---
title: "How I got my Linksys WMP300n working on Ubuntu 9.10"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by DogoDave on 2010-03-10
Okay I have worked on this for a long time and have had several skilled linux people help but we just never seemed to be able to get my wireless card to work.  Well I have finally done so and I happened to manage the whole thing myself so I am going to put down what I did so that others with the same problem may be able to get theirs working too.  

**The end solution is using ndiswrapper** which I had been trying to use all along

First things first.... I had the feeling that all the previous attempts to get this card working had somehow corrupted the installation.  I'm not sure where, or how, or if it is even possible in Ubuntu, but coming from a long history with Microsoft this thought was impossible to ignore.  So I set out to completely remove ndswrapper and the wireless driver 

To remove ndiswrapper completely I found the following web page: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Uninstall_HowTo]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Uninstall_HowTo") 
Now I still don't understand all the commands in terminal and when the instructions tell me to use the locate command and the updatedb command and such I try but I don't always know if one command actually did anything or not(as it turns out the updatedb wouldn't work for me).  The way I followed these instructions is the way a Windows user would be able to understand.** Warning the following gives you root access within a browser window and you can easily delete important files so be careful.**

To open a browser window that has full permissions within folders(you will need this to be able to delete the files) you type the following command in a terminal
```
sudo nautilus --browser 
```

Now that you have that browser open go to the top panel and click on Places>Search for Files... when the search box opens change the "Look in Folder" to say File System and then in the "Name Contains" box type **ndiswrapper** and click "Find".  In the search results you will see any files and folders that have that name and their location is displayed to the right.  Using that browser that we opened earlier I navigated to each folder and each file that appeared in the list and I deleted them.  After you delete a folder you can click "Find" again on the search window and it will update the list clearing out the ones that you have deleted and showing you what you still have remaining to remove.

Repeat the above method to remove all files and folders pertaining to **ndiswrapper**, and **loadndisdriver**. This ends the cleanup portion of what I did **now Reboot** just because I don't know when Ubuntu needs to reboot and when it doesn't, but in Windows this would be the time to do it so I did it here.  

next part coming up...

---

### Post by DogoDave on 2010-03-10
Now for the installing portion

Check out this video 
[http://www.youtube.com/watch?v=v0Ist9aEKEg]("http://www.youtube.com/watch?v=v0Ist9aEKEg")

I tried to follow this video but the guy changes from root and back a few times and whenever he was able to open a directory my terminal said that "no such file or directory exist" so I had to do things a little differently.

First do use the commands to find out about your card...turns out I didn't need this info for anything but if you require it use these
```

lspci

and 

lspci -n

```

Okay so moving past that, I did do what the man in the video suggests and made a folder in the directory /usr/src named ndiswrapper-1.56 as that is the current version as of writing this...I downloaded the ndiswrapper-1.56.tar.gz file and put it in that directory(/usr/src/ndiswrapper-1.56) You will again need to have a browser open that has permission to create that folder there so again us the nautilis command below to open the browser and create the directory and put the files into it.  Keep this browser window open because you will need to put more file into that directory shortly.
```
sudo nautilus --browser
```

At this point in the video the guy uses terminal to extract the .tar file but since I am using that browser window I just double clicked on the **ndiswrapper-1.56.tar.gz ** and hit extract, it will extract to a folder with the same name and that is that(make sure you are already in the directory specified above as it just make it easier to keep the files in that directory)

The next part of the video he says to use the command "make" but that did nothing for me in Ubuntu 9.10 so I looked up and found that a better command to use for me is 
```
sudo apt-get install build-essential
```
This does what he was saying about getting all the ....well essentials needed 

Next he uses the "make install" but that doesn't work for me either...it is at this point that we leave the video as it no longer is of any use to me. My next stop is over to 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") **THE REMAINDER OF THIS POST PERTAINS TO INFO FOUND ON THIS WEB PAGE**
  
and I pretty much followed it exactly and it worked but I'll quickly go through it. 


First: 

Click on System>Administration>Software Sources check to make sure that the 2nd and 4th boxes are selected don't change anything else just make sure that those one are selected.  These are the universe and multiverse repositories.


Second:

use ```
sudo apt-get install ndisgtk
```this may tell you that you already have the current version and that is fine.


Third:

Under section 2.2.1 Currently Supported Releases 
For 9.10 Karmic Koala which is Ubuntu 9.10 **download each of the files in the list** and again using that nautilis browser command open a browser and put all those files into the /usr/src/ndiswrapper-1.56 directory that you made earlier.


Almost done but we need to be able to have root control in terminal so open terminal and use
```
su
``` if that works you will see that in terminal instead of it saying **your-username@your-username-desktop:/$** it will change to **root@your-username-desktop:/#**  If you get an error or it won't let you use root control you'll have to do the following.  Click on System>Administration>Users and Groups when the window opens you'll have to click on those keys to let you make changes and then enter your password....once you have done that then highlight root and click "properties" and give the root user a password(DO NOT FORGET IT) then click OK....Now if you go back to terminal and typr su it should prompt you for a password type in the password that you just gave the root user and it should let you in.(**FOR THE ABOVE INSTRUCTIONS REGARDING ROOT CONTROL I KNOW VERY LITTLE ABOUT USING ROOT CONTROL AND DON'T KNOW IF YOU EVEN NEED TO CREATE A PASSWORD OR IF YOU CAN JUST GIVE THE COMMAND IN TERMINAL AND US YOUR OWN PASSWORD TO CHANGE TO ROOT, I HAD PREVIOUSLY SET UP A PASSWORD IN AN ATTEMPT TO BE ABLE TO LOGIN AS ROOT USER.  I SUGGEST JUST TRYING THE COMMAND WITHOUT ACTUALLY MAKING A ROOT USER PASSWORD**

So now to finish of only 3 commands in terminal as the root user and we are done....

First type to change directories to the one that you created```
cd /usr/src/ndiswrapper-1.56
```

Then one at a time type each of the following
```
sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils-*.deb
sudo dpkg -i ndisgtk_*.deb
```

You should see it will tell you that things are missing and then it will say something like preparing to restore such and such **anyway when everything is done..... disconnect your ethernet cable and reboot...** 

When your running again check up on the top panel in the notification area and there should be a network monitor icon click on it select the network you want to connect to and provide the required encryption key.(I won't get into connecting to a network because if you can get this far I am sure you know how)

Anyway that's it...I thought I would put it down for anyone else with this card that was having problems.  This is what I did and I am making these post from my wireless connection.  The funny thing is, is that an experienced Linux user might be able to tell exactly which part of this is what made it work and which parts were unnecessary but regardless this is how I did it.

---

### Post by kkobashi on 2011-05-26
You shouldn't have to do any of the things above. Tonight, I took an old Ubuntu 9.10 CD and did an install on an old desktop PC.

The desktop PC had the Linksys Wireless WMP300N already inside the box. Simply boot the CD and install. Then, go to the System | Preferences | Network Connections.

Click on the Wireless tab. Then Add a connection. Set the SSID. Then go to the wireless security and choose, say WEP 40/128. Then, enter in your WEP password. A dialog box should pop up again, it may ask for the WEP key. Enter it in again and you should go live.

---

