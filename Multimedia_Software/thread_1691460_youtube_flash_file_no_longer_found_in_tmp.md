---
title: "youtube flash file no longer found in tmp"
date: 2011-02-19
forum: Multimedia Software
---

### Post by aa4bb on 2011-02-19
Until recently, after I watched a YouTube video in Firefox, the flash file would be found in the tmp folder immediately after the video finished playing. This was handy, because I could just copy and paste it to another location to save it.

Now it doesn't show up there. I haven't changed any settings, to my knowledge.

If it is still being cached but to a different location, I'd love to know where.

---

### Post by steveneddy on 2011-02-19
I noticed that recently myself.

.... WOA

---

### Post by PaulReaver on 2011-02-19
guys this was discussed less than an hour ago...??? search button? 

[http://ubuntuforums.org/showthread.php?t=1690673](http://ubuntuforums.org/showthread.php?t=1690673)




here you'll find this usefull

paste this little lot into a text file and save it.. then right click properties and make it executable... it'll dump any OPEN flash videos to your home directory... 




#!/bin/bash

args=("$@")

args=`echo $args | sed 's/[/]$//'`

pids=`eval pgrep -f flashplayer`
for pid in $pids
do
lsoutput=$(lsof -p $pid | grep '/tmp/Flash[^ ]*')

IFS=$'\n'
for line in $lsoutput; do
lsout1=`echo $line | awk '{print "/proc/" $2 "/fd/" $4}' | sed 's/[rwu]$//'`
lsout2=`echo $line | awk '{print $9}' | awk -F '/' '{print $3}'`

if [ -n "$args" ];then
if [ -d $args ]; then
echo "Copying $lsout2 to $args/"
eval "cp $lsout1 $args/$lsout2.flv"
else
echo "The directory \"$args\" doesn't exist"
break
fi
else
echo "Copying $lsout2"
eval "cp $lsout1 $lsout2.flv"
fi

done
done

---

### Post by aa4bb on 2011-02-22
Excellent! Many thanks, PaulReaver!

---

### Post by chetancrasta on 2011-02-25
While you can get the flash videos from firefox's cache, it is not as convenient and reliable as getting it from the /tmp directory.

Therefore, if you want to restore this 'feature', you will need to downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

### Post by tmy on 2011-03-07
> **chetancrasta said:**
> While you can get the flash videos from firefox's cache, it is not as convenient and reliable as getting it from the /tmp directory.

Therefore, if you want to restore this 'feature', you will need to downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.
Hello [chetancrasta]("http://newyork.ubuntuforums.org/member.php?u=763415"),  first let me say thank you for your fantastic advice it looks to be the  best way around this problem. I have a problem I can't for the life of  me figure out how to carry out your instructions. I downloaded the files  I needed and managed to extract the libflashplayer.so but this where I  get stuck I don't understand command line I'm sorry I try but it is so  confusing.

I have the files in a folder on my desktop ( easy to find :-) ) my user name is "s" and my question is this because you know where my folder  is with the file I need inside ( libflashplayer.so ) could you please  show me the code I need to have rights and over write the file at   /usr/lib/flashplugin-installer

Please be gentle I love Ubuntu and manage really well most of the time but command line is hard and I hate to mess up my system.

I got as far as cp libflashplayer.so  /usr/lib/flashplugin-installer but  it didn't like it and I suspect I needed to start off with sudo or  similar please if you could help out it would be greatly appreciated.

Thank you take care.

tmy

---

### Post by chetancrasta on 2011-03-07
> **tmy said:**
>  I downloaded the files  I needed and managed to extract the libflashplayer.so but this where I  get stuck I don't understand command line I'm sorry I try but it is so  confusing.

I got as far as cp libflashplayer.so  /usr/lib/flashplugin-installer but  it didn't like it and I suspect I needed to start off with sudo or  similar please if you could help out it would be greatly appreciated.

Thank you take care.

tmy

What you need to do is open Nautilus (Ubuntu's File Manager) with root privileges.
One way to do this is to press Alt-F2 and then type ```
gksudo nautilus
``` and press Enter. You can then copy the libflashplayer.so file to the /usr/lib/flashplugin-installer directory.
Another way of opening Nautilus with root privileges is to type gksudo nautilus in Terminal.

---

### Post by tmy on 2011-03-07
Hi    	chetancrasta,
thank you for getting back to me but I'm just as confused     :( I have opened the Nautilus but that's it I have clicked on desktop but nothing happens how can I copy and paste the file into /usr/lib/flashplugin-installer directory ?

I'm really lost sorry to be a pain but please step by step I want to learn but I have no clue, sorry...................:confused:

Thank you for your help take care 


tmy

---

### Post by chetancrasta on 2011-03-07
> **tmy said:**
> Hi    	chetancrasta,
 I have opened the Nautilus but that's it I have clicked on desktop but nothing happens how can I copy and paste the file into /usr/lib/flashplugin-installer directory ?
tmy

When you open Nautilus with gksudo, and then open the Desktop folder in it, you will see the Desktop of the user "root".

Therefore, you should do this: first open Nautilus normally, navigate to Desktop (or where ever the libflashplayer.so file is located). Then open gksudo nautilus and navigate to the /usr/lib/flashplugin-installer directory. Then drag libflashplayer.so file from the first nautilus window into the second.

---

### Post by tmy on 2011-03-07
> **chetancrasta said:**
> When you open Nautilus with gksudo, and then open the Desktop folder in it, you will see the Desktop of the user "root".

Therefore, you should do this: first open Nautilus normally, navigate to Desktop (or where ever the libflashplayer.so file is located). Then open gksudo nautilus and navigate to the /usr/lib/flashplugin-installer directory. Then drag libflashplayer.so file from the first nautilus window into the second.
Hi [chetancrasta]("http://ubuntuforums.org/member.php?u=763415"),
thank you so much your instructions were really clear and I managed to over write the libflashplayer.so file and all is back to the way I'm used to with the tmp folder being the one the flash file appears in when it's finished playing so I can rename and cut to a permanent location.

This is the ONLY way that is acceptable for me and we have  [chetancrasta]("http://ubuntuforums.org/member.php?u=763415") to thank for some really great work taking time to post the solution and taking time to walk inexperienced users through the process showing patience and understanding to help. 

Thank you so much can't express enough my gratitude.   Take care  


tmy

---

### Post by chetancrasta on 2011-04-10
Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

---

### Post by satish_j on 2011-04-19
> **chetancrasta said:**
> 

extract libflashplayer.so and overwrite the file at /usr/lib/**flashplugin-installer** (you will need root privileges, try gksudo nautilus)



flashplugin-installer is a file or folder??If it is a folder,i cannot find any folder with such name in /usr/lib.
Pls reply..

---

### Post by chetancrasta on 2011-04-19
> **satish_j said:**
> flashplugin-installer is a file or folder??If it is a folder,i cannot find any folder with such name in /usr/lib.
Pls reply..

Then perhaps Flash is not installed? You need to have Flash installed before you follow the procedure.
Anyway, it is better that you don't downgrade Flash (for security reasons). Use this script: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
It is more convenient and works with current versions of Flash.

---

### Post by satish_j on 2011-04-20
does this script works when the video is completely loaded or will it start saving video the moment it is started in browser?
Previously,it was getting saved in /tmp folder instantly and i liked that feature very much.

---

### Post by chetancrasta on 2011-04-20
> **satish_j said:**
> does this script works when the video is completely loaded or will it start saving video the moment it is started in browser?
Previously,it was getting saved in /tmp folder instantly and i liked that feature very much.

Why don't you try it out? The script just saves the temp video file whether it is full or not.

---

### Post by satish_j on 2011-04-20
okay..one last question...
Where is the video file saved?
In /tmp or any other path?

---

### Post by chetancrasta on 2011-04-20
> **satish_j said:**
> okay..one last question...
Where is the video file saved?
In /tmp or any other path?

The default is the current directory but, using a command line switch, that can be changed.

---

### Post by wkulecz on 2011-04-20
If you are using Firefox, why not just install the "Download Helper" plugin?

---

### Post by madjr on 2011-04-20
flash videos are now in firefox cache.

you also control the cache size within firefox preference.

i bookmarked the firefox cache directory for quick access.

---

### Post by chetancrasta on 2011-04-20
> **wkulecz said:**
> If you are using Firefox, why not just install the "Download Helper" plugin?

Because none of the plugins downloaded the buffered video. Instead, they ignore the buffered video in the cache and always download the video a second time.

---

### Post by nitstorm on 2011-04-20
Try this one....   /[http://thevoidghost.wordpress.com/2011/03/22/flash-cache-on-ubuntu-linux/](http://thevoidghost.wordpress.com/2011/03/22/flash-cache-on-ubuntu-linux/)

---

### Post by chetancrasta on 2011-04-20
> **madjr said:**
> flash videos are now in firefox cache.

you also control the cache size within firefox preference.

i bookmarked the firefox cache directory for quick access.

The problem with trying to get the buffered video from the cache is that the browser's cache size should be larger than the buffered video. What if the buffered video is several GB? One would have to specify a very large cache size.
The script mentioned earlier negates the need to mess with cache settings.

---

### Post by satish_j on 2011-04-22
I cannot run the script..getting foll error
```

satish@MyGet:~$ /home/satish/Desktop/Script.sh
ERROR:  Couldn't find any deleted cached flash files

Usage:	Script.sh [-d]
  Copies deleted flash files currently open in your browser's cache
  -d             Set debug mode
  -find <str>    What to search for  [default flash]
  -post <str>    Postfix for saving files [default flv]
  -dest <str>    Or just specify full destination [default found%f.%d%p]
                 (see the script for meanings of %f, %d, %p)

```
any ideas?

---

### Post by chetancrasta on 2011-04-22
> **satish_j said:**
> I cannot run the script..getting foll error
```

satish@MyGet:~$ /home/satish/Desktop/Script.sh
ERROR:  Couldn't find any deleted cached flash files

Usage:	Script.sh [-d]
  Copies deleted flash files currently open in your browser's cache
  -d             Set debug mode
  -find <str>    What to search for  [default flash]
  -post <str>    Postfix for saving files [default flv]
  -dest <str>    Or just specify full destination [default found%f.%d%p]
                 (see the script for meanings of %f, %d, %p)

```
any ideas?

Some flash videos have copy protection and cannot be saved [http://kb2.adobe.com/cps/405/kb405456.html](http://kb2.adobe.com/cps/405/kb405456.html)
You haven't mentioned whether it happens with one video or all. It makes sense to test the script with a few different videos. Also, which version of Flash were you using?

---

### Post by satish_j on 2011-04-23
i tried the script,but it saves vid only when it is completely loaded in browser.
Iam looking for something which will save vid as soon as it is started and will continue to save the streaming vid to the point it is closed.
If,for ex,after watching 1 min of video,i intend to close the vid,i copy the file in /tmp and save somewhere else and then close the browser window playing vid.
The copied file will be of 1 min duration,which i want.
what say??

---

### Post by chetancrasta on 2011-04-26
> **satish_j said:**
> i tried the script,but it saves vid only when it is completely loaded in browser.

Uh, the script does save partially loaded Flash videos.
I'm surprised that you're finding it so difficult to use a script that just has to be double clicked to run.

---

### Post by greenjumper on 2011-05-08
> **chetancrasta said:**
> Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

Nice little script - thanks a lot for this!

---

### Post by aa4bb on 2011-05-27
> **chetancrasta said:**
> Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.
chetancrasta, thank you so much for this helpful response to my original thread post. I just revisited the thread after having considered it [SOLVED], only to find the additional postings.

---

### Post by amirmku on 2012-05-20
> **PaulReaver said:**
> guys this was discussed less than an hour ago...??? search button? 

[http://ubuntuforums.org/showthread.php?t=1690673](http://ubuntuforums.org/showthread.php?t=1690673)




here you'll find this usefull

paste this little lot into a text file and save it.. then right click properties and make it executable... it'll dump any OPEN flash videos to your home directory... 




#!/bin/bash

args=("$@")

args=`echo $args | sed 's/[/]$//'`

pids=`eval pgrep -f flashplayer`
for pid in $pids
do
lsoutput=$(lsof -p $pid | grep '/tmp/Flash[^ ]*')

IFS=$'\n'
for line in $lsoutput; do
lsout1=`echo $line | awk '{print "/proc/" $2 "/fd/" $4}' | sed 's/[rwu]$//'`
lsout2=`echo $line | awk '{print $9}' | awk -F '/' '{print $3}'`

if [ -n "$args" ];then
if [ -d $args ]; then
echo "Copying $lsout2 to $args/"
eval "cp $lsout1 $args/$lsout2.flv"
else
echo "The directory \"$args\" doesn't exist"
break
fi
else
echo "Copying $lsout2"
eval "cp $lsout1 $lsout2.flv"
fi

done
done

sorry but I couldn't figure out how to use this script.
As per instruction above I have copy and pasted the script in text editor saved and with right click set the properties to executable file.
but after playing any youtube video flash files do not appear in home directory. please help.

---

### Post by oldos2er on 2012-05-20
We do not support violating Youtube's TOS: [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

Thread closed.

---

