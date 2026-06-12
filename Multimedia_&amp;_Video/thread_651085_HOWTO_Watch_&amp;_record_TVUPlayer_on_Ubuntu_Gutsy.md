---
title: "HOWTO: Watch &amp; record TVUPlayer on Ubuntu Gutsy + Wine"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by Pavcio on 2007-12-27
Here is tutorial to watch&record TVUPlayer which is also on tvunetworks forums.

1. At first we should install Windows emulator: Wine
> sudo apt-get install wine

2. Then we should install Windows Media Player from this tutorial
> [http://tinyurl.com/2jtyll](http://tinyurl.com/2jtyll)

3. Then install TVUPlayer - The newest version doesn't work very well so the best version is "v2.3.3beta2[build788] 

> 
cd /Directory where setup is 
then 
wine Setup.exe

4. Now we can easily run the TVUPlayer (by deafult it is set like this)
> 
cd /home/user_name/.wine/drive_c/Program Files/TVUPlayer
wine TVUPlayer.exe

5. When it's running we can't see any channel names so open file 
> gedit /home/user_name/.wine/drive_c/Program Files/TVUPlayer/ChannelList.xml

and simply count the channels first on  this file and they are in the same order in the list in program

6. Start channel by clicking him and wait a little bit.

7. Press X on the right top of the program but don't exit him, just close

8. Install Mplayer when you don't have it
> sudo apt-get install mplayer


9.Type in console 
> mplayer -fs 127.0.0.1:8901


And voila you can play it but how to record it?
Do everthing the same till point 8 and after it type in console:
> mplayer [http://127.0.0.1:8901](http://127.0.0.1:8901) -dumpstream  -dumpfile stream.asf -cache 8192 -forceidx

And it should be as stream.asf in the folder where you are now. This is not perfect but in my way any way to record it. 


Any suggestions?

---

### Post by jjrp78 on 2008-01-09
Do you have by any chance the 2.3.3 beta 2 version? I cant find it any where do you have a link from where I could download it?

---

### Post by SB-X on 2008-04-22
Has anyone actually tried this and confirmed that it works? I can't get past the "install Windows Media Player" step. The author doesn't explain everything and links to an old post on his blog that says it's out of date and not to use it anymore.

Also I can't get sound working in Wine no matter what driver I select in winecfg.

EDIT: Sound started working on it's own the second time I launched winecfg, and WMP9 installed succesfully after setting quartz.dll and devenum.dll to Native in the libraries tab of winecfg. But TVU and Wine crash as soon as any (blank) channel is clicked on. (it's TVUPlayer version 2.3.0 so that might be the problem)

EDIT2: WOW it's really working now! I'm surprised. TVUPlayer v2.3.6 this time. Of course, the thing takes minutes to start, is extremely slow, doesn't have it's entire UI, and I'd probably use up fewer resources actually running it under VMWare, but the point is it actually runs and sends video that mplayer will play! It's at least worth it for the ability to record shows this way.

Just an addendum to the instructions: To play it in MPlayer you must prepend *"http://"* to the address.
The new version does run, but it starts too slow, and you can't see UI just like the OP described.
The ChannelList.xml isn't under "Program Files". It isn't at "C:\WINDOWS\profiles\<username>\Local Settings\Application Data\TVU Networks\TVUPlayer" or anywhere under "Documents & Settings" either.
Ubuntu 7.10 Gutsy

---

### Post by Wiebelhaus on 2008-04-23
> **SB-X said:**
> Has anyone actually tried this and confirmed that it works? I can't get past the "install Windows Media Player" step. The author doesn't explain everything and links to an old post on his blog that says it's out of date and not to use it anymore.

Also I can't get sound working in Wine no matter what driver I select in winecfg.

EDIT: Sound started working on it's own the second time I launched winecfg, and WMP9 installed succesfully after setting quartz.dll and devenum.dll to Native in the libraries tab of winecfg. But TVU and Wine crash as soon as any (blank) channel is clicked on. (it's TVUPlayer version 2.3.0 so that might be the problem)

EDIT2: WOW it's really working now! I'm surprised. TVUPlayer v2.3.6 this time. [COLOR="Red"]Of course, the thing takes minutes to start, is extremely slow, doesn't have it's entire UI, and I'd probably use up fewer resources actually running it under VMWare, but the point is it actually runs and sends video that mplayer will play![/COLOR] It's at least worth it for the ability to record shows this way.

Just an addendum to the instructions: To play it in MPlayer you must prepend *"http://"* to the address.
The new version does run, but it starts too slow, and you can't see UI just like the OP described.
The ChannelList.xml isn't under "Program Files". It isn't at "C:\WINDOWS\profiles\<username>\Local Settings\Application Data\TVU Networks\TVUPlayer" or anywhere under "Documents & Settings" either.
Ubuntu 7.10 Gutsy

This stuck me as funny , anyway - I'mma try it!

---

### Post by uberstuber on 2008-05-27
> **jjrp78 said:**
> Do you have by any chance the 2.3.3 beta 2 version? I cant find it any where do you have a link from where I could download it?

I would like to find this as well, everywhere online claiming to have it just links to the new version.

---

### Post by moreinfo on 2008-06-01
Hi,

I get to the ...


"We now need to install MSCAT32.dll and change the version from win2k to winxp and the install should finish."

and have no idea what this means...
can someone help.

It's straight after installing the windows 9 media... 

Thanks in advance

---

