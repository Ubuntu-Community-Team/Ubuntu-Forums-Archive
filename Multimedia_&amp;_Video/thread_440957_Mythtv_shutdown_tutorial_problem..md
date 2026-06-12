---
title: "Mythtv shutdown tutorial problem."
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by Rictus on 2007-05-12
Hi, I'm having problems getting this tutorial to work.

[http://ubuntuforums.org/showthread.php?t=351184&highlight=shutdown+button+%2B+mythtv](http://ubuntuforums.org/showthread.php?t=351184&highlight=shutdown+button+%2B+mythtv)

I think it may stem from my earlier problems of my login being different in my backend then in myth.

I log in myth as mythtv but in my server as rick. So my mythtv directory would be here /home/mythtv/.mythtv and also here /home/rick/.mythtv. I thnk this causes problems when I use something like ~/.mythtv/mythscript, I don't know which one it's supposed to go in or which one it actually does.
 I have the shutdown button in myth but it doesn't do anything. I think I need to copy some files from one directory to the other or something like that.
Can anyone tell me what to type in to get the script working properly?
Thanks
Rick

---

### Post by wjston on 2007-05-13
> **Rictus said:**
> Hi, I'm having problems getting this tutorial to work.

[http://ubuntuforums.org/showthread.php?t=351184&highlight=shutdown+button+%2B+mythtv](http://ubuntuforums.org/showthread.php?t=351184&highlight=shutdown+button+%2B+mythtv)

I think it may stem from my earlier problems of my login being different in my backend then in myth.

I log in myth as mythtv but in my server as rick. So my mythtv directory would be here /home/mythtv/.mythtv and also here /home/rick/.mythtv. I thnk this causes problems when I use something like ~/.mythtv/mythscript, I don't know which one it's supposed to go in or which one it actually does.
 I have the shutdown button in myth but it doesn't do anything. I think I need to copy some files from one directory to the other or something like that.
Can anyone tell me what to type in to get the script working properly?
Thanks
Rick

Did you create the directory "mythscript" in ~/.mythtv and place the shutdown script in that directory? If so, right click on the script and check to see that it is executable by the user mythtv - look in properties to see who owns the script. If it is owned by root, mythtv will not be able to launch the script.

---

### Post by Rictus on 2007-05-13
Thanks for the reply. 
I'm sorry to be such a noob but I don't know how to check that from the terminal. Is there a way to use a gui on a server?
I don't know how to see what files are in a directory.

I did check this: the file shutdown.sh is in /home/rick/.mythtv/mythscript
but not in /home/mythtv/.mythtv/mythscript

Sorry.
Rick

---

### Post by wjston on 2007-05-13
> **Rictus said:**
> Is there a way to use a gui on a server?
I don't know how to see what files are in a directory.

Actually, I created this script to shutdown a system running as both a frontend and backend. If you are trying to shutdown just a frontend, I believe mythtv is already setup to do this......check the forums on shutting down the frontend. That said, I don't know if this will work on just a frontend.[COLOR="Blue"] This link may has information on shutting down a server when it is idle: [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)[/COLOR]


> I did check this: the file shutdown.sh is in /home/rick/.mythtv/mythscript
but not in /home/mythtv/.mythtv/mythscript

Sorry.
Rick

The file shutdown.sh should be placed in /home/mythtv/.mythtv/mythscript in order for the Shutdown button to work (**<action> EXEC ~/.mythtv/mythscript/shutdown.sh </action>**). However, this will only shutdown the frontend and not the backend (server). I apologize for not reading your post correctly last night. Could you explain a little more as to what you are trying to do with this script - I too am relatively new to linux/mythtv having only set up my mythboxes approximately one year ago.

---

### Post by Rictus on 2007-05-13
I'll try to explain myself better. I want to be able to use the remote control to click and have the entire box shut off. Backend and frontend.
You are correct I can do this to the frontend. 
I was thinking it wasn't working because it wasn't in the correct directory.
 
What I was trying to say in my eariler post was that I don't know how to right click on the file. The only way I can view it is in the terminal, that I know of, and you can't right click on it in there.
 
I've been trying to mkdir in the /.mythtv/mythscript directory and trying to cp from my rick directory to the mythtv directory but nothing seems to be working. I still have no file in my /home/mythtv/.mythtv/mythscript directory
 
I don't know the proper way to copy. I'm just trying to copy this:
```
/home/rick/.mythtv/mythscript/shutdown.sh
```
to this:
```
/home/mythtv/.mythtv/mythscript/shutdown.sh
```
 
I hope that explains it a little better.
Rick

---

### Post by wjston on 2007-05-13
> **Rictus said:**
> I'll try to explain myself better. I want to be able to use the remote control to click and have the entire box shut off. Backend and frontend.
You are correct I can do this to the frontend. 
I was thinking it wasn't working because it wasn't in the correct directory.
 
What I was trying to say in my eariler post was that I don't know how to right click on the file. The only way I can view it is in the terminal, that I know of, and you can't right click on it in there.
 
I've been trying to mkdir in the /.mythtv/mythscript directory and trying to cp from my rick directory to the mythtv directory but nothing seems to be working. I still have no file in my /home/mythtv/.mythtv/mythscript directory
 
I don't know the proper way to copy. I'm just trying to copy this:
```
/home/rick/.mythtv/mythscript/shutdown.sh
```
to this:
```
/home/mythtv/.mythtv/mythscript/shutdown.sh
```
 
I hope that explains it a little better.
Rick

If you have a separate backend and frontend, this script will not work as far as I know. I am running a combined frontend/backend mythbox. I created this script to shutdown my system because I have another system that was built using MythDora. MythDora was designed to shut down a system using a remote and I really missed this feature when I built my second pvr. 

If the script enables you to turn off your frontend now, then you may need to configure your server to shut down using the way the previous link I posted suggests. As far as copying files from one directory to another, you should be able to do this as easy as "sudo cp  ip_of_server/home/rick/.mythtv/mythscript/shutdown.sh ~/.mythtv/mythscript/shutdown.sh 
You need to be in a terminal in the frontend box. An easier way would just redo the script from a terminal in the frontend and create the necessary directory and script as per the guide. However, I don't believe that this will enable you to shut down your backend using the shutdown button.

---

### Post by Rictus on 2007-05-14
I'm sorry, still not making myself very clear. I'm good (or bad) at that. My setup is a combination frontend/backend in one box. When I click shutdown when in mythtv it does nothing. But as you say I can hit esc and it shuts down myth and goes to the backend where I can access the terminal.
My thinking (which may be wrong) is because the script isn't in the right folder. 
I tried the "cp" command but it wouldn't work. It said the directory or something didn't exist.
Sorry to be such a pain.
Rick

---

### Post by newlinux on 2007-05-14
Rick,

This thread is confusing :). I'm not saying these things to be critical, but just to help clarify things for you. When you close the mythfrontend it is not really going to the "mythbackend" but rather to a console  (text based) terminal session. The mythbackend is always running in the background - and you don't really "log into" it in this manner. I think that is where you confused some into thinking your frontend and backend where different machines. Really what is happening is that the GUI on your machine (combined frontend/backend) is closing when you close mythtv (mythfrontend). It isn't that you are dropping into "server" mode or anything. You should be able to access some GUI options by closing mythfrontend. you are probably running openbox, which doesn't come preconfigured with nice menus and desktop panels like gnome and kde. But you should be able to access some menu item with the mouse... But I can't say for certain, as I didn't install it this way.

Are you sure the directory /home/mythtv/.mythtv/mythscript exists (your error indicates something doesn't exist)? It could be that you typed in something incorrectly as well (wrong name of a directory or something). It would be helpful to know exactly what you typed and exactly what the error message was. If the directory doesn't exist, assuming you are logged in as "rick" try:

```

sudo -u mythtv mkdir /home/mythtv/.mythtv/mythscript
sudo -u mythtv cp /home/rick/.mythtv/mythscript/shutdown.sh /home/mythtv/.mythtv/mythscript/

```

And just to make sure, assuming that command above worked  and the file is in /home/mythtv/.mythtv/mythscript/ do :
```

sudo -u mythtv chmod +x /home/mythtv/.mythtv/mythscript/shutdown.sh

```
If you are logged in as mythtv you can omit the "sudo -u mythtv" portions.


Based on this and the last issue I helped you with, I think you might have really been helped out by having a regular ubuntu desktop on your myth machine so you could use the GUI tools that maybe you are more familiar with. 
You can install it by doing:

```

sudo aptitude install ubuntu-desktop

```

NOTE: I am unsure of how it will mess with your current setup of myth autologin and all that.  So use with caution. It shouldn't  mess up your mythbox or anything like that, just maybe some of the automatic login things. If you don't want to take any chance of messing with that don't do it. It will also take a lot of time to install a lot of packages.

---

### Post by wjston on 2007-05-14
> **Rictus said:**
> I'm sorry, still not making myself very clear. I'm good (or bad) at that. My setup is a combination frontend/backend in one box. 
Rick

Rick,
When you installed Ubuntu, which version did you use (desktop, server, alternate)? Also, which guide did you follow when you installed MythTV?

---

### Post by Rictus on 2007-05-16
Sorry. I am a bit lost on some of the terms that are thrown around in Ubuntu. 
I used this tutorial.
[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)
 
Newlinux:
When i type in the mkdir command it says:
mkdir: cannot create directory '/home/mythtv/.mythtv/mythscript': File exists.
 
And when I type in the cp command it says:
cp: accessing '/home/mythtv/.mythtv/mythscript/': Not a directory.
 
This doesn't seem right. How can it say "file exists" and "not a directory" at the same time?
It doesn't have anything to do with the slash "/" at the end does it?
 
Thanks...again.

---

### Post by newlinux on 2007-05-16
No, somehow you have a file called mythscript instead of a directory mythscript. You don't need the ending slash with mkdir because it only makes directories.

try 

```

rm /home/mythtv/.mythtv/mythscript

```

and then try the commands I wrote above.

---

### Post by Rictus on 2007-05-17
hmmm...doesn't seem to be working. After I type in the rm command it askes if I want to remove it, what do I do then? I tried typing a y, but it said it couldn't remove it. So I tried again and just hit enter, then it went to a prompt so I tried the mkdir and got the same "file exists" error.
grrr.

---

### Post by newlinux on 2007-05-17
You need to have the right permissions to remove it. So if you aren't logged in as mythtv you need to put

sudo -u mythtv 

in front of the command like earlier. You would answer yes to removing it.

```

sudo -u mythtv rm /home/mythtv/.mythtv/mythscript

```

---

### Post by Rictus on 2007-05-18
OK I now have shutdown.sh file in the correct place, but when I run that chmod command it does nothing and the button still doesn't work. So there is something else wrong.

---

### Post by wjston on 2007-05-18
> **Rictus said:**
> OK I now have shutdown.sh file in the correct place, but when I run that chmod command it does nothing and the button still doesn't work. So there is something else wrong.

Try changing ownership of the shutdown.sh file using this command (change to the mythscript directory prior to running the command):

cd ~/.mythtv/mythscript
chown -R mythtv:shutdown.sh

and if necessary, chmod 777 shutdown.sh

Note: you may have to use sudo in front of these commands!

Hopefully this gets your button working. Please post your results.

---

### Post by Rictus on 2007-05-19
I get an error from chown.
chown: missing opperand after 'mythtv:shutdown.sh'
I tried putting -L at the end but got the same error.
Any ideas?
Thanks.

---

### Post by wjston on 2007-05-19
> **Rictus said:**
> I get an error from chown.
chown: missing opperand after 'mythtv:shutdown.sh'
I tried putting -L at the end but got the same error.
Any ideas?
Thanks.

You may have to be Root to do this - $ [COLOR="Red"]sudo su[/COLOR] and then your password.

The easiest way to fix this would be to add gnome desktop and then log in as root user. Then, go to the directory mythscript, locate the script shutdown.sh, right-click on it and choose Properies>Permissions, and then change ownership to mythtv and group to mythtv. Just follow the guide here to allow root user to login in gnome: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_root_user_to_login_into_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_root_user_to_login_into_GNOME)

If installing gnome stops mythtv from logging in first, there is lots of information on how to set this up in the forums. Setting this up will only take a couple of minutes.

Hope this helps.

---

### Post by Rictus on 2007-05-19
Ok, got gnome installed although I can't seem to figure out how to login as root. There is no option to do so, it just says login to gnome. I clicked allow local system admin.
But I do see a problem, when I right click on the shutdown.sh file it says owner is mythtv but group is shutdown.
Could this be the problem?

---

### Post by newlinux on 2007-05-19
You probably don't really want to enable to root account. You should be able to do everything you need with sudo. In ubuntu, by default, the root account is disabled for security reasons. You can do

```
sudo -i
```


to be in a root shell, but this is not advised since you can just prepend sudo to whatever command. When you are done type

```
exit
```


According to the tutorial you posted earlier, it should be owned by mythtv and it should be in the shutdown group.


```
ls -l /home/mythtv/.mythtv/mythscript/shutdown.sh

```
return?

Did you add mythtv to the shutdown group, as the tutorial indicates? Did you also modify the sudo user access to the shutdown command? (the parts where it says as Root) in the tutorial.

---

### Post by Rictus on 2007-05-20
> 
Code:
ls -l /home/mythtv/.mythtv/mythscript/shutdown.sh
return?

 
```
 
-rwxrwxrwx 1 mythtv shutdown 244 2007-05-18 03:13 [COLOR=lime]/home/mythtv/.mythtv/mythscript/shutdown.sh[/COLOR] 

```
 
Any help?

---

### Post by newlinux on 2007-05-20
Yeah, the file is in the right group, owned by the right user, and has the right permissions. Something else must be wrong. What about the adding mythtv to the shutdown users and all of that that I asked in the earlier post? I have to be honest, I'm just going by the tutorial too, as I don't use this, but based on the tutorial, that file looks fine.

---

### Post by Rictus on 2007-05-20
I think I did everything correctly there. But with my screwy file structure it's hard to say.
One thing that is weird is I don't see a /home/rick/mythtv/.mythv directory only /home/rick/.mythtv
I'm wondering if I haven't been typing in the wrong directory or something. 
The shutdown.sh file in my /home/rick/.mythtv/mythscript directory has ownership of root.
Is this ok?

---

### Post by newlinux on 2007-05-20
> **Rictus said:**
> I think I did everything correctly there. But with my screwy file structure it's hard to say.
One thing that is weird is I don't see a /home/rick/mythtv/.mythv directory only /home/rick/.mythtv
I'm wondering if I haven't been typing in the wrong directory or something. 
The shutdown.sh file in my /home/rick/.mythtv/mythscript directory has ownership of root.
Is this ok?

Yeah, that's all correct. The /mythtv/ shouldn't be in /home/rick. If you are running mythtv as the mythtv user what's in /home/rick shouldn't matter.

---

### Post by Rictus on 2007-05-20
Can I copy everything from that directory over to the /home/mythtv/.mythtv directory?

---

### Post by newlinux on 2007-05-20
yes. just make sure the permissions are set correctly and files are owned by the right user when moved. using sudo -u mythtv before copying should do that, if you are logged in as rick. If you are logged in as mythtv regular copying should do it.

---

### Post by wjston on 2007-05-20
> **Rictus said:**
> 
But I do see a problem, when I right click on the shutdown.sh file it says owner is mythtv but group is shutdown.
Could this be the problem?

Hi Rictus,
The way you have the shutdown.sh file is correct now. The owner should be mythtv and the group should be shutdown (sorry for mentioning group as mythtv in my earlier post). Setting up the "Group - Shutdown" and changing the shutdown.sh script to this group is just a security precaution. Only users of this group will be able to launch this script.

---

### Post by wjston on 2007-05-20
> **Rictus said:**
> I think I did everything correctly there. But with my screwy file structure it's hard to say.
One thing that is weird is I don't see a /home/rick/mythtv/.mythv directory only /home/rick/.mythtv
I'm wondering if I haven't been typing in the wrong directory or something. 
The shutdown.sh file in my /home/rick/.mythtv/mythscript directory has ownership of root.
Is this ok?

You will not have a directory /home/rick/mythtv/.mythtv. The shutdown script must be located in /home/mythtv/.mythtv/mythscript in order for it to work. Mythtv is the user that needs to launch this script. If you only have this script located in your home directory, then mythtv cannot launch it. Also, this part of the tutorial - 
Then
"As Root: # visudo
Add: shutdown ALL= NOPASSWD: /sbin/halt, /sbin/shutdown"
(without the quotes) will only be saved if you are root. You can try typing "sudo visudo" and then enter the user password as requested.

---

### Post by wjston on 2007-05-20
> **Rictus said:**
> Ok, when I right click on the shutdown.sh file it says owner is mythtv but group is shutdown.
Could this be the problem?

Check to make sure "Allow executing file as program" is checked at the bottom of the permissions tab in the properties box of the shutdown.sh script.

---

### Post by Rictus on 2007-05-22
Ya, it's checked.
So, there are only three parts to make this work right?
The button, the script, and the permissions. 
So it has to be the communication between the button and the script somehow???
What tells the button to execute the script?

---

### Post by wjston on 2007-05-23
> **Rictus said:**
> Ya, it's checked.
So, there are only three parts to make this work right?
The button, the script, and the permissions. 
So it has to be the communication between the button and the script somehow???
What tells the button to execute the script?

The user mythtv is the one who executes the script after the "button" is pressed. The script has to be owned by MythTV ("permissions"), and the script itself calls the application executable "shutdown" located in the directory /sbin. The only thing that I can think of is that maybe MythTV does not have "Read and write" access to the shutdown.sh script. You can check this by going into the properties of the script and clicking on the "Permissions" tab - look under Owner>Access and make sure the drop down is set to "Read and write." Also, check to make sure the "location of the script" (under the Basic Tab) is the same as the location in the shutdown.sh script (<action> EXEC [COLOR="Red"]~/.mythtv/mythscript/shutdown.sh[/COLOR] </action>). If your unsure, copy the location from the properties box and paste it into the script.

---

### Post by Rictus on 2007-05-27
OK all that seems to be right. Read and write permissions look ok.
When I tried to open the script in gnome it shut down everything, I ran it and it shut the computer down. So it seems to work that way.
>  
If your unsure, copy the location from the properties box and paste it into the script.

Not sure what you mean by that, but it says the right location. So I guess it doesn't matter.
 
OK there are two things I may have done wrong but by what you say to check everything looks ok.
1. The first part of your tutorial says as myth user and the second part says as root. I don't think I did that because I don't know how.
2. Your tutorial uses **~/.mythtv/mythscript **which is actually the wrong directory on my computer because it goes to /home/rick/.mythtv not /home/mythtv/.mythtv.
But I redid the tutorial once and according to our conversation everything has been put in the right location.
Is there anything from these two parts that could be causing a problem, such as a duplicate file in /home/rick/.mythtv? According to newlinux mythtv should just ignore this right?
 
Thats all I can think of.
 
How do I log in as myth user and then switch to root?
 
OK say that I wasn't logged in as myth user when I created the button. Could this be the problem? I mean could this cause it not to execute properly?

---

### Post by Rictus on 2007-05-29
Well, I had to change my password to log in as mythtv because none of my passwords would work.
I was trying to redo the button, but when I try to cp the mainmenu.xml file or try to suo nano to onpn it I get an error. Permission denied and mythtv is not in the sudoers file. This will be repoerted.???

---

### Post by wjston on 2007-05-29
> **Rictus said:**
> Well, I had to change my password to log in as mythtv because none of my passwords would work.
I was trying to redo the button, but when I try to cp the mainmenu.xml file or try to suo nano to onpn it I get an error. Permission denied and mythtv is not in the sudoers file. This will be repoerted.???

What I would do is add mythtv to the sudoers group until you get everything copied over. You can do this through your user by bringing up a terminal and typing in sudo nano /etc/group. Scroll down until you see sudo:x:27: and add mythtv to the end (no space - :mythtv). You will be prompted for a password and you should be able to do everything a normal user can.

---

### Post by Rictus on 2007-05-29
hmmm, didn't work same errors.

---

### Post by wjston on 2007-05-29
> **Rictus said:**
> Well, I had to change my password to log in as mythtv because none of my passwords would work.

When you log in as Mythtv user, if you go to >Places>Home Folder, is the Mythscript folder and Shutdown.sh file that  you created there?

---

### Post by Rictus on 2007-06-03
Yes. It's in the mythscript folder which is in the .mythtv folder which is in the mythtv folder.
 
Now I know how to log in as myth user, is there anything I can try to run to see whats going on.
 
One thing I confused about is logging as root. Not sure I understand this. Does this mean to log in as my main user, i.e. rick?

---

### Post by wjston on 2007-06-03
> **Rictus said:**
> Yes. It's in the mythscript folder which is in the .mythtv folder which is in the mythtv folder.
 
Now I know how to log in as myth user, is there anything I can try to run to see whats going on.
 
One thing I confused about is logging as root. Not sure I understand this. Does this mean to log in as my main user, i.e. rick?

No. You would type "root" in as the user and then whatever password you set up following the link [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_root_user_to_login_into_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_root_user_to_login_into_GNOME). What you could try first is bring up a terminal and start mythtv that way (type "mythfrontend">press Enter). Once you have it running, try shutting down using the shutdown button. Nothing will probably happen, but what ever is preventing the script form running or shutting down mythtv should be recorded in the terminal and you will be able to review it once you back out of mythtv (use what ever button you normally use on your remote - mine is the "Back/Exit" button). Copy and Paste the output concerning the shutdown button in your next post and I will see what else we can do to get this operational.

---

### Post by Rictus on 2007-06-03
This is from within gnome, I also did it from within openbox. The openbox output was almost identical except for the line about gnome screensaver.
 
 
```
 
$ mythfrontend 
X Error: BadDevice, invalid or uninitialized input device 169 
Major opcode: 148 
Minor opcode: 3 
Resource id: 0x0 
Failed to open device 
X Error: BadDevice, invalid or uninitialized input device 169 
Major opcode: 148 
Minor opcode: 3 
Resource id: 0x0 
Failed to open device 
2007-06-03 09:05:15.755 Using runtime prefix = /usr 
2007-06-03 09:05:15.766 Gnome-Screensaver support enabled 
2007-06-03 09:05:15.767 DPMS is active. 
2007-06-03 09:05:15.792 New DB connection, total: 1 
2007-06-03 09:05:15.798 Connected to database 'mythconverg' at host: localhost 
2007-06-03 09:05:15.799 Total desktop dim: 1280x1024, with 1 screen[s]. 
2007-06-03 09:05:15.802 Using screen 0, 1280x1024 at 0,0 
2007-06-03 09:05:15.817 Current Schema Version: 1160 
2007-06-03 09:05:15.817 mythfrontend version: 0.20.20060828-3 www.mythtv.org 
2007-06-03 09:05:15.817 Enabled verbose msgs: important general 
2007-06-03 09:05:16.251 Total desktop dim: 1280x1024, with 1 screen[s]. 
2007-06-03 09:05:16.252 Using screen 0, 1280x1024 at 0,0 
2007-06-03 09:05:16.253 Switching to square mode (blue) 
2007-06-03 09:05:16.413 Using the Qt painter 
2007-06-03 09:05:16.967 Joystick disabled. 
2007-06-03 09:05:16.996 Loading from: /usr/share/mythtv/themes/default/base.xml 
2007-06-03 09:05:17.571 Registering Internal as a media playback plugin. 
2007-06-03 09:05:30.015 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5) 
2007-06-03 09:05:30.017 Using protocol version 31 
$ 

```

---

### Post by wjston on 2007-06-03
> **Rictus said:**
> This is from within gnome, I also did it from within openbox. The openbox output was almost identical except for the line about gnome screensaver.
 
 
```
 
$ mythfrontend 
X Error: BadDevice, invalid or uninitialized input device 169 
Major opcode: 148 
Minor opcode: 3 
Resource id: 0x0 
Failed to open device 
X Error: BadDevice, invalid or uninitialized input device 169 
Major opcode: 148 
Minor opcode: 3 
Resource id: 0x0 
Failed to open device
```

Don't be concerned about this. This is an error referencing Wacom Tablet and can be resolved by removing a few lines in your xorg.cong file (I wouldn't be concerned about it).

> 2007-06-03 09:05:15.755 Using runtime prefix = /usr 
2007-06-03 09:05:15.766 Gnome-Screensaver support enabled 
2007-06-03 09:05:15.767 DPMS is active. 
2007-06-03 09:05:15.792 New DB connection, total: 1 
2007-06-03 09:05:15.798 Connected to database 'mythconverg' at host: localhost 
2007-06-03 09:05:15.799 Total desktop dim: 1280x1024, with 1 screen[s]. 
2007-06-03 09:05:15.802 Using screen 0, 1280x1024 at 0,0 
2007-06-03 09:05:15.817 Current Schema Version: 1160 
2007-06-03 09:05:15.817 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org) 
2007-06-03 09:05:15.817 Enabled verbose msgs: important general 
2007-06-03 09:05:16.251 Total desktop dim: 1280x1024, with 1 screen[s]. 
2007-06-03 09:05:16.252 Using screen 0, 1280x1024 at 0,0 
2007-06-03 09:05:16.253 Switching to square mode (blue) 
2007-06-03 09:05:16.413 Using the Qt painter 
2007-06-03 09:05:16.967 Joystick disabled. 
2007-06-03 09:05:16.996 Loading from: /usr/share/mythtv/themes/default/base.xml 
2007-06-03 09:05:17.571 Registering Internal as a media playback plugin. 
2007-06-03 09:05:30.015 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5) 
2007-06-03 09:05:30.017 Using protocol version 31 
$ 
[/code]

Did you press the "Shutdown" button from within MythTV frontend? If you did, there is no reference to that process here, which means MythTV is not even executing the command at all.

---

### Post by Rictus on 2007-06-03
Ya, I move to it with the remote and cliked OK a few times. Just to make sure, when I was in openbox I also hit enter on the keyboard a few times when I had the shutdown button highlighted.
Hopefully this gives you an idea....I hope.

---

### Post by wjston on 2007-06-03
> **Rictus said:**
> Ya, I move to it with the remote and cliked OK a few times. Just to make sure, when I was in openbox I also hit enter on the keyboard a few times when I had the shutdown button highlighted.
Hopefully this gives you an idea....I hope.

I have to tell you I am a bit confused that there wasn't any output to the terminal when you pressed the shutdown button. When I was setting this up, I used the terminal as my problem solver. It basically told me steps I needed to complete in order to get this script to work.

I'm curious, when you got to the step in the guide that said "As Root:
# groupadd shutdown
# nano /etc/group
Add "mythtv" (without quotes) to end of shutdown group
Then
As Root: # visudo
Add: shutdown ALL= NOPASSWD: /sbin/halt, /sbin/shutdown," did you actually complete this step as a Root User? If you did not see  the # sign in the terminal, you were still logged in as a normal user with the $ sign. However, I think you should have been asked for a password when you clicked on the shutdown button in order to continue.

---

### Post by wjston on 2007-06-03
> **Rictus said:**
> Ya, I move to it with the remote and cliked OK a few times. Just to make sure, when I was in openbox I also hit enter on the keyboard a few times when I had the shutdown button highlighted.
Hopefully this gives you an idea....I hope.

Rictus, check to make sure there aren't any spaces in the following lines of your mainmenu.xml file.
$ sudo nano /usr/share/mythtv/mainmenu.xml
Add the following to the end of mainmenu.xml
<button>
<type>MENU_UTILITIES_SETUP</type>
<text>Shutdown</text>
<action>EXEC ~/.mythtv/mythscript/shutdown.sh</action>
</button>

 I was going over the tutorial, and I noticed a space between some of the entries so I corrected them. Hopefully, this is why your button is not communicating with the script. Also, make sure the above entry is one space above the closing entry "</mythmenu>" (without the quotes).

Hopefully this is why your script is not communicating with the button.

---

### Post by Seneca on 2007-06-05
I too was having a problem with this script not actually doing anything.  I fixed mine by adding a % before "shutdown" in visudo.  I think that "%" denotes groups, and since there was no "%" I think it was trying to grant privileges to a non-existent "shutdown" user.

---

### Post by wjston on 2007-06-05
> **Seneca said:**
> I too was having a problem with this script not actually doing anything.  I fixed mine by adding a % before "shutdown" in visudo.  I think that "%" denotes groups, and since there was no "%" I think it was trying to grant privileges to a non-existent "shutdown" user.

Seneca, thanks for pointing out the "%" addition to the script. I never had it in mine as I added mythtv to the admin group in  "/etc/group" because I needed to control a satellite receiver and this was one of the suggestions in one of the posts I followed to get mythtv to control my dish. I tried removing mythtv from admin in /etc/group and the shutdown button would not communicate with the script. When I added the % sign to the beginning of  [COLOR="Blue"]shutdown ALL= NOPASSWD: /sbin/halt, /sbin/shutdown[/COLOR] the button worked. I added the change to the script so it should work now. It sure helps to get feedback from other users when something goes wrong on other systems.

Thanks again for helping to narrow down this problem. 

Rictus, could you let me know if this helps to resolve your situation.

---

### Post by Rictus on 2007-06-07
>  
Rictus, check to make sure there aren't any spaces in the following lines of your mainmenu.xml file.
$ sudo nano /usr/share/mythtv/mainmenu.xml
Add the following to the end of mainmenu.xml
<button>
<type>MENU_UTILITIES_SETUP</type>
<text>Shutdown</text>
<action>EXEC~/.mythtv/mythscript/shutdown.sh</action>
</button>

 
OK I fixed this and now my shutdown button in myth has a picture of a wrench and a key on it like the settings button. So this must have done something. Unfortunately it still doesn't work.
I added the % in front of the shutdown line in visudo.
 
>  
did you actually complete this step as a Root User?

 
I think I used sudo -s to do that part if I remember correctly.
 
```
 
<action>EXEC~/.mythtv/mythscript/shutdown.sh</action>

```
 
I think the above line is linked to my user directory. Can I change it to:
```
 
<action>EXEC/home/mythtv/.mythtv/mythscript/shutdown.sh</action>

```
 
???

---

### Post by wjston on 2007-06-07
> **Rictus said:**
> OK I fixed this and now my shutdown button in myth has a picture of a wrench and a key on it like the settings button. So this must have done something. Unfortunately it still doesn't work.
I added the % in front of the shutdown line in visudo.
 

 
I think I used sudo -s to do that part if I remember correctly.

You have to complete this step as Root user or it will not work. I think typing "sudo visudo" in a terminal and then entering your password may allow you to save the % in front of the shutdown line so that it will work. If not, I know typing "sudo nano /etc/group" and adding mythtv to the end of the admin user will give mythtv the necessary privileges to execute the shutdown command (that is how I have mine set up).
 
> ```
 
<action>EXEC~/.mythtv/mythscript/shutdown.sh</action>

```
 
I think the above line is linked to my user directory. Can I change it to:
```
 
<action>EXEC/home/mythtv/.mythtv/mythscript/shutdown.sh</action>

```
 
???

The ~/ in the first line actually means /home/mythtv/ so you can change it if you want and it shouldn't make any difference. The best way to check that you are actually pointing to the shutdown.sh script is to go the script through >Places>Computer>Filesystem>Home>Mythtv>Location/Directory/shutdown.sh then right click on the script, click Properties and check the location of the script. However, I am sure you probably have it in the right place, but the privilege problem is what is stopping you from executing the shutdown.sh script.

---

### Post by Rictus on 2007-06-17
My visudo has the % at the beginning of the shutdown line so I think thats ok. 
 
In the /etc/group directory I have a line that starts lpadmin and one that starts admin. Are one of these line the ones your talking about? Neither one of theses have mythtv listed after them. 
 
I changed the mainmenu.xml file like I mentioned earlier. Didn't seem to work either.

---

### Post by wjston on 2007-06-17
> **Rictus said:**
> My visudo has the % at the beginning of the shutdown line so I think thats ok. 
 
In the /etc/group directory I have a line that starts lpadmin and one that starts admin. Are one of these line the ones your talking about? Neither one of theses have mythtv listed after them. 
 
I changed the mainmenu.xml file like I mentioned earlier. Didn't seem to work either.

Add mythtv after the admin user. Then, start mythtfrontend from a terminal and try shutting down using the button. Hopefully, this will either work or give you some info as to why it isn't.

---

### Post by Rictus on 2007-06-30
ug..I got new problems now. Had to rob the video card (ATI 9800pro) and put in ATI 9200.
Now I get x server error at boot up. ](*,)
 
OK got that Fixed now.

---

### Post by Rictus on 2007-06-30
OK adding mythv to admin line didn't seem to do anything. Here's my group file.
 
```
 
 
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:rick
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:rick,mythtv,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:rick,mythtv,haldaemon
floppy:x:25:rick,haldaemon
tape:x:26:
sudo:x:27:mythtv
audio:x:29:rick,mythtv
dip:x:30:rick
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:rick,mythtv
sasl:x:45:
plugdev:x:46:rick,haldaemon
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:rick,cupsys,hplip
nvram:x:105:
crontab:x:106:
ssh:x:107:
rick:x:1000:
lpadmin:x:108:rick
admin:x:109:rick,mythtv
mysql:x:110:
mythtv:x:111:rick
ntp:x:112:
gdm:x:113:
messagebus:x:114:
shutdown:x:1001:mythtv
ssl-cert:x:115:cupsys
stunnel4:x:116:
avahi-autoipd:x:117:
avahi:x:118:
netdev:x:119:
haldaemon:x:120:
powerdev:x:121:haldaemon
postfix:x:122:
postdrop:x:123:
saned:x:124:
slocate:x:125:

```

---

### Post by wjston on 2007-07-10
```
 
<action>EXEC~/.mythtv/mythscript/shutdown.sh</action>

```
 
I think the above line is linked to my user directory. Can I change it to:
```
 
<action>EXEC/home/mythtv/.mythtv/mythscript/shutdown.sh</action>

```
 
???[/QUOTE]

This is the only thing that I can think is preventing the script from executing. If you saved the file on your (rick) desktop, then I would either try changing the location in the <action>EXEC/home/ line to your name -  <action>EXEC/home/rick/Desktop/mythscript/shutdown.sh</action>, or redoing this section of the guide so that you have the script saved to the mythtv desktop.

---

