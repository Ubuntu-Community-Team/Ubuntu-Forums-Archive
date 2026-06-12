---
title: "How is everyone viewing Hulu and fancast in mythtv?"
date: 2009-09-09
forum: Mythbuntu
---

### Post by williammanda on 2009-09-09
How is everyone viewing Hulu and fancast in mythtv?

---

### Post by blackoper on 2009-09-11
I created a menu item on the main myth menu to allow me to quickly get to Boxee. It works great for all the online video sites including hulu.

To do this:
Install boxee and get a username for it
edit mainmenu.xml file
sudo nano /usr/share/mythtv/mainmenu.xml
add this entry and save:

   <button>
     <type>TV_WATCH_RECORDINGS</type>
     <text>Launch Boxee</text>
     <action>EXEC /opt/boxee/run-boxee-desktop</action>
   </button>


you will now have a boxee option on your main myth menu. Once you exit boxee it will bring you right back into myth.

---

### Post by ahood on 2009-09-11
Also use firefox launched from within the mythbuntu frontend, see [http://ubuntuforums.org/showpost.php?p=7805356&postcount=16](http://ubuntuforums.org/showpost.php?p=7805356&postcount=16)

---

### Post by williammanda on 2009-09-11
> **blackoper said:**
> I created a menu item on the main myth menu to allow me to quickly get to Boxee. It works great for all the online video sites including hulu.

To do this:
Install boxee and get a username for it
edit mainmenu.xml file
sudo nano /usr/share/mythtv/mainmenu.xml
add this entry and save:

   <button>
     <type>TV_WATCH_RECORDINGS</type>
     <text>Launch Boxee</text>
     <action>EXEC /opt/boxee/run-boxee-desktop</action>
   </button>


you will now have a boxee option on your main myth menu. Once you exit boxee it will bring you right back into myth.

My understanding is that Boxee is only 32 bit now. Will that work with 64 bit?
Thanks

---

### Post by williammanda on 2009-09-11
> **ahood said:**
> Also use firefox launched from within the mythbuntu frontend, see [http://ubuntuforums.org/showpost.php?p=7805356&postcount=16](http://ubuntuforums.org/showpost.php?p=7805356&postcount=16)

How do you launch firefox with Hulu would be my first question?

> E. In the Mythtv frontend, navigate to...
Home --> Setup --> Utilities/Setup --> Info Settings --> Web
For the browser launch text box, replace default text with the following line
/usr/bin/firefox-wrapper

What mythtv option do you have installed?

Thanks

---

### Post by ahood on 2009-09-12
> **williammanda said:**
> How do you launch firefox with Hulu would be my first question?



Firefox will be the default browser that Mythweb will launch. thus, simply add a mythweb bookmark for Hulu within the MythTV Frontend. 

> **williammanda said:**
> What mythtv option do you have installed?

Mythbrowser

I hope this helps.

---

### Post by williammanda on 2009-09-12
Ahood
I have mythweb installed but I don't have the setup you describe. I only know how to access mythweb via firefox. Are you referring to mythbrowser?
Thanks

---

### Post by ahood on 2009-09-13
> **williammanda said:**
> Ahood
I have mythweb installed but I don't have the setup you describe. I only know how to access mythweb via firefox. Are you referring to mythbrowser?
Thanks

Yes, my bad. Myth browser is the plugin. Much apologies.

---

### Post by silverdulcet on 2009-09-13
> **williammanda said:**
> My understanding is that Boxee is only 32 bit now. Will that work with 64 bit?
Thanks

It works just fine under 64 bit. It just requires a few 32-bit libraries which can be automatically downloaded by a script called getlibs. Someone even wrote a script that will install everything automatically and you can re-run it to check for updates. If there is one it will download and install the updated version. 

See this post in the boxee forums:
[http://forum.boxee.tv/showpost.php?p=59280&postcount=57]("http://forum.boxee.tv/showpost.php?p=59280&postcount=57")

Since I'm still running intrepid, I've altered line 10 from "jaunty" to "intrepid" for the [http://apt.boxee.tv/dists/intrepid](http://apt.boxee.tv/dists/intrepid) link.

The script checks if you have the getlibs script installed, and if not then downloads it and installs it. Then checks the boxee repository for the newest version of Boxee and downloads the deb file, then installs it. If you already have the latest version nothing happens. Finally it runs getlibs to make sure that you have all the 32 bit libraries required by Boxee.

Save the script as boxeeinstall.sh. Make it executable:
```
chmod +x boxeeinstall.sh
```
Then run the script. It will ask you for the sudo password since installing deb packages requires sudo privileges.
  
```
#!/bin/bash

if [ "`which getlibs`" == "" ]; then
  wget -O /tmp/getlibs-all-$$.deb 
  http://frozenfox.freehostia.com/cappy/getlibs-all.deb
  sudo dpkg -i /tmp/getlibs-all-$$.deb
  rm /tmp/getlibs-all-$$.deb
fi

wget -qO /tmp/boxee-packages-$$.gz http://apt.boxee.tv/dists/intrepid/main/binary-i386/Packages.gz
LATEST=`zgrep Version /tmp/boxee-packages-$$.gz | awk '{v=0; for (i = 1; i <= NF; i++) if ($2 > v) v = $2}; END {print v}'`
echo "LATEST: $LATEST"
CURRENT=`dpkg -s boxee 2> /dev/null | awk '/Version/ {print $2}'`
echo "CURRENT: $CURRENT"

if [ "$LATEST" != "$CURRENT" ]; then
  wget -O /tmp/boxee-$$.deb http://apt.boxee.tv/`zgrep Filename /tmp/boxee-packages-$$.gz | tail -n1 | awk '{print $2}'`
  sudo dpkg -i --force-all /tmp/boxee-$$.deb
  rm /tmp/boxee-$$.deb
  getlibs /opt/boxee/Boxee
fi

rm /tmp/boxee-packages-$$.gz

```

---

### Post by uncle hammy on 2009-09-13
Thanks for the script, I actually downgraded my machine to 32bit at the beginning of the summer just to have Boxee.  After reading your post, I reinstalled my machine with 64bit again, and it got Boxee going!  I did have one hiccup however.  When I tried to log in, I kept getting an "Internet Connection Unavailable" error.  

For anyone else that tries this script, and runs into the same problem, I resolved it by running:
```
sudo aptitude install lib32nss-mdns
```
as per here [http://forum.boxee.tv/showthread.php?t=3188](http://forum.boxee.tv/showthread.php?t=3188)

---

### Post by silverdulcet on 2009-09-13
> **uncle hammy said:**
> Thanks for the script, I actually downgraded my machine to 32bit at the beginning of the summer just to have Boxee.  After reading your post, I reinstalled my machine with 64bit again, and it got Boxee going!  I did have one hiccup however.  When I tried to log in, I kept getting an "Internet Connection Unavailable" error.  

For anyone else that tries this script, and runs into the same problem, I resolved it by running:
```
sudo aptitude install lib32nss-mdns
```
as per here [http://forum.boxee.tv/showthread.php?t=3188](http://forum.boxee.tv/showthread.php?t=3188)

Thanks, I neglected to post that since its been a while since I installed Boxee on my 64 bit system. Its a good idea to keep an eye on this thread for specific issues with running boxee releases under 64bit linux:

[http://forum.boxee.tv/showthread.php?t=4980]("http://forum.boxee.tv/showthread.php?t=4980")

And this part of the forum for information on Boxee on linux in general as well as sound issues, etc. 

[http://forum.boxee.tv/forumdisplay.php?f=4]("http://forum.boxee.tv/forumdisplay.php?f=4")

---

### Post by williammanda on 2009-09-14
I got Boxee install and setup in mythtv. I like most everything but one main issue. The volume control. It seems there are two volume problems.
1. When using an application like Hulu, you can't adjust the volume.
2. When viewing local videos, the volume works but it only goes as high as the master volume (in ubuntu) is set.
So for both of these issues I have two use "\" to reduce Boxee to a window then adjust the master volume.
I read over alot of the posts in their forum but I haven't found a fix yet.
Thanks

---

### Post by silverdulcet on 2009-09-14
>  	
Re: How is everyone viewing Hulu and fancast in mythtv?
I got Boxee install and setup in mythtv. I like most everything but one main issue. The volume control. It seems there are two volume problems.
1. When using an application like Hulu, you can't adjust the volume.
2. When viewing local videos, the volume works but it only goes as high as the master volume (in ubuntu) is set.
So for both of these issues I have two use "\" to reduce Boxee to a window then adjust the master volume.
I read over alot of the posts in their forum but I haven't found a fix yet.
Thanks 

I'd encourage you to make a new post here and perhaps in that Boxee linux forum an ask if anyone might know a solution. Since I have my Mythbuntu system hooked up to my receiver via spdif I use the receiver's controls to adjust the volume.

---

### Post by dsauter on 2009-09-15
Wouldn't it be great if the Mythbuntu control center had an option to add all this Boxee stuff we have to do manually?  It even sounds like the 64 bit hang up has a relatively nice work-around now.  Myth really, really needs to add streaming support and it seems like most of us are using Boxee to perform this.

---

### Post by tgm4883 on 2009-09-15
> **dsauter said:**
> Wouldn't it be great if the Mythbuntu control center had an option to add all this Boxee stuff we have to do manually?  It even sounds like the 64 bit hang up has a relatively nice work-around now.  Myth really, really needs to add streaming support and it seems like most of us are using Boxee to perform this.

Great news! Mythbuntu control centre is plugable. This means you can create your own plugin and distribute it. Grab the branch at [https://code.edge.launchpad.net/~mythbuntu/mythbuntu/mythbuntu-control-centre](https://code.edge.launchpad.net/~mythbuntu/mythbuntu/mythbuntu-control-centre)

MythTV is also plugable, see info here [http://www.mythtv.org/wiki/Plug-in_developers_guide](http://www.mythtv.org/wiki/Plug-in_developers_guide)

---

### Post by williammanda on 2009-09-15
> **silverdulcet said:**
> I'd encourage you to make a new post here and perhaps in that Boxee linux forum an ask if anyone might know a solution. Since I have my Mythbuntu system hooked up to my receiver via spdif I use the receiver's controls to adjust the volume.

I don't know much about spdif but how does that get you around the volume control issue I have?

---

### Post by crez79 on 2009-09-15
You can make a script with this in it:
```
amixer set Master playback 100%
```and the command to launch boxee, and it will set the Master playback volume to 100%, then launch boxee. I am not sure how, but I am sure someone can make some script magic to watch for boxee to exit and then set the volume to something lower.

Spdif outputs the sound signal directly to the receiver, and then the volume control is adjusted from the receiver, so the mixer doesn't have any effect on the volume.

---

### Post by williammanda on 2009-09-16
Crez79
I apprecaite the script idea but it doesn't fully address both the issues. It does for one but not the other. When viewing Hulu (via boxee)...there is not volume control. You have to use the master volume control. It's the same if you view Hulu from a browser.
Thanks

---

### Post by azmyth on 2009-09-16
May want to try this suggestion.

[http://forum.boxee.tv/showthread.php?t=11108](http://forum.boxee.tv/showthread.php?t=11108)

I haven't tried this yet.

I have a problem of low volume in all of Boxee even with Boxee's volume at max as well as MB.

---

### Post by williammanda on 2009-09-17
> **azmyth said:**
> May want to try this suggestion.

[http://forum.boxee.tv/showthread.php?t=11108](http://forum.boxee.tv/showthread.php?t=11108)

I haven't tried this yet.

I have a problem of low volume in all of Boxee even with Boxee's volume at max as well as MB.

Yes I have seen that post and I don't want to go to that extreme. I can view Hulu via a browser and adjust the volume just as easy. Either they will fix it or I just won't use boxee.

---

### Post by azmyth on 2009-09-18
> **azmyth said:**
> May want to try this suggestion.
I have a problem of low volume in all of Boxee even with Boxee's volume at max as well as MB.

I ended up writing two bash scripts one to store the original volume and then change to 2 x original then start boxee and then another to restore and restart the frontend. If anyone wants, let me know and I'll post. You'll need irexec going though.

---

### Post by williammanda on 2009-09-18
> **azmyth said:**
> I ended up writing two bash scripts one to store the original volume and then change to 2 x original then start boxee and then another to restore and restart the frontend. If anyone wants, let me know and I'll post. You'll need irexec going though.

Please post it.
Thanks

---

### Post by azmyth on 2009-09-18
I'm surely no bash expert so feel free to make changes and post. Add these two scripts to your /home/username directory and chmod +x


restartmyth.sh
```
#!/bin/bash

if [ ! $(pidof -x mythfrontend.real) ]; then
#Read in the saved value from starting boxee
for WORD in `cat /home/mythtv/test.txt`
do
echo > /dev/null
done

#####################################################################
# Set volume.
function set_volume()
{
    amixer cset iface=MIXER,name="Master Playback Volume" $1 >/dev/null
}

#Start the frontend and reset volume to the original
/usr/bin/mythfrontend &
set_volume $WORD
fi
exit 0;

```

```
#!/bin/bash
#

#####################################################################
# Get current volume.
function get_volume()
{
    mixer=$(amixer get Master | grep 'Front Left:')
    echo $mixer | cut -d ' ' -f 4

}

#####################################################################
# Set volume.
function set_volume()
{
    amixer cset iface=MIXER,name="Master Playback Volume" $1 >/dev/null
}


    ovol=$(get_volume)
    echo $ovol > test.txt

#Change the number 2 to something that works with your system
    vol=`echo $ovol*2 | bc`
    set_volume $vol
    kill -9 `pidof -x mythfrontend.real`
    cd /opt/boxee
   ./run-boxee-desktop

 exit 0;

```

Add this to /usr/share/mythtv/themes/defaultmenu/mainmenu.xml
```
<button>
<type>TV_WATCH_RECORDINGS</type>
<text>Launch Boxee</text>
<action>EXEC /home/mythtv/startboxee.sh</action>
</button>
```

In my /home/username/.boxee/UserData/Lircmap.xml I specified one of my remote buttons as power. The power will kill boxee for you.

```
<power>b</power>
```

Make the changes to you lircrc file and make sure repeat is commented out.
```
begin
        prog = irexec
        button = b
        #repeat = 3
        config = /home/mythtv/restartmyth.sh
end

```

---

