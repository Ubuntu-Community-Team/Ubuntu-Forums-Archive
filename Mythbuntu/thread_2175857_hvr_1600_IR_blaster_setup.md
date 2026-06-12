---
title: "hvr 1600 IR blaster setup"
date: 2013-09-21
forum: Mythbuntu
---

### Post by qsilver7 on 2013-09-21
I was able to get the remote working in Myth and the blaster to send using Jays tutorial as referenced in
[http://ubuntuforums.org/showthread.php?t=2137294](http://ubuntuforums.org/showthread.php?t=2137294)
but have not been able to figure out how to get it to send the proper codes for my receiver through mythtv.

SOLVED (This assumes you are already watching and recording your stb in mythtv)

Just needed to figure out the finer details. 
I created the scripts using 
sudo gedit
and edited the files using 
sudo gedit /*path*/*to*/*what ever the file name is* 
After changing anything in lirc, save and restart lirc to get the changes recognised by running
sudo /etc/init.d/lirc restart
First was place the Jays blaster codes 
[http://www.blushingpenguin.com/mark/lmilk/lircd.conf](http://www.blushingpenguin.com/mark/lmilk/lircd.conf)
in the hauppauge lirc file. The hauppauge lirc path is in /etc/lirc/lirc.conf 
Restart lirc
Not knowing anything about scripts, it took a while to figure out I had to make the channel change script in Jays post executable, [http://www.blushingpenguin.com/mark/lmilk/send_power_new](http://www.blushingpenguin.com/mark/lmilk/send_power_new)
so I could run it and find my power code.
All the scripts required the entire path to the file, even the sudo chmod command. I put everything in /home/mythtv, so it was simply 
sudo chmod 755 /home/mythtv/send_power_new.sh
to make it executable
With the blaster attached to the stb ir receiver, I ran 
/home/mythtv/send_power_new.sh
and watch the output until the power went off the stb. When I tried to test the code with irsend in terminal
irsend SEND_ONCE blaster[COLOR=#000000] 0_29_KEY_POWER
[/COLOR]it didnt work, so I tried
irsend SEND_ONCE blaster[COLOR=#000000] 1_28_KEY_POWER
[/COLOR]and it worked. I simply saw the change in terminal 1 code late. If you run send_power_new.sh and it doesn't work, make sure you have placed the blaster on the stb ir receiver properly (cover the spot with something and try your stb remote. If it doesn't work, it's the right spot) and try again. 
If it still doesn't work, the script probably doesn't have your stb remote codes, so your done here. good luck
Still here? Great. Now you can clean up your remote blaster codes.
Mine were 1_28, so I deleted everything from 
[COLOR=#000000]name 0_1_KEY_0 to [/COLOR][COLOR=#000000]name 0_28_KEY_DISPLAY [/COLOR][COLOR=#000000]1835029
[/COLOR][COLOR=#000000]and [/COLOR][COLOR=#000000]name 0_29_KEY_0 *to* [/COLOR][COLOR=#000000]name 1_731_KEY_Off [/COLOR][COLOR=#000000]2195390542 leaving the line "end raw_codes". Don't delete the hauppauge remote codes.
[/COLOR][COLOR=#000000]For the script I used for channel change in myth, i needed to delete 1_28_KEY_ from each code. This is done easily in gedit using Replace in the Search menu. For me, it was SEARCH FOR 1_28_KEY_ and leave REPLACE WITH blank. Click Replace All and your done. Save and restart lirc

For the channel change script, I used Mark's from [/COLOR][http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24) (please note the last line about beer)
[COLOR=#000000]The script is at [/COLOR]http://www.blushingpenguin.com/mark/lmilk/change_channel
[COLOR=#000000]Again, I saved changechannel.pl in /home/mythtv
For me, blaster was correct and needs_enter=0 was correct, but the location for irsend was wrong. I googled how to search for a file and searched the entire hard drive to find irsend. No idea how long the search took as I left the room. When I came back, my search had found it at /usr/bin/irsend.
Make sure this line is correct and save.
[/COLOR]sudo chmod 755 /home/mythtv/changechannel.pl
[COLOR=#000000]I tested channel 302 in terminal with
[/COLOR]/home/mythtv/changechannel.pl $SIGNAL 302
[COLOR=#000000]it worked, so I put it in mythbackend under Input Connection as my external channel change script. Again, use the full path
[/COLOR]/home/mythtv/changechannel.pl
[COLOR=#000000]
If you've read this far, you, like me, were probably close to reaching the end of the internet trying to figure out how to get this to work. Hopefully this helps.


[/COLOR]

---

