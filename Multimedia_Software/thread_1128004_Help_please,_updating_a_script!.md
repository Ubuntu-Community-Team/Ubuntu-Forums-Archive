---
title: "Help please, updating a script!"
date: 2009-04-17
forum: Multimedia Software
---

### Post by einnar on 2009-04-17
I have a script that I found on [[COLOR="Red"]THIS[/COLOR]]("http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php?t=3250529#c3250529") post a while back.

The link to the script is [[COLOR="Red"]here[/COLOR]]("http://cct-public.s3.amazonaws.com/ripdvd"). It'll download it to your machine if you click that link, but I'll attach the code at the end of this post if you don't want to do that.

With one of the more recent Ubuntu updates, it's stopped working for me, and the original author can't be reached.

Can someone take a look at this, and tell me if it can be updated? Scripting is foreign to me, and I'm just spinning my wheels trying to figure it out. I love this script, though, and have used it to copy my collection to my HD, then used AcidRip to turn them all into AVIs so that I can take my collection on the road with me. (I travel a lot, and it's easier to carry them on a 1TB HD than as individual movies..) I own every movie that I do this to. 

I'm using 8.04 (Hardy)
Thanks!

```

#!/bin/bash

# set -x

function setTitle () {
    echo -n "]0;$1"
}


umask 022

dvd_device=$1
shift

sub=$1
shift

termTitle="RIP $dvd_device"

if [ "$sub" = "" ] ; then
	if [ "$DISPLAY" = "" ] ; then
		export DISPLAY=:0
	fi
	gnome-terminal -t "$termTitle" -e "$0 $dvd_device sub 2>&1 | tee -a /var/tmp/ripdvdsub.log"
	exit 0
fi

size=`df -h $dvd_device | grep $dvd_device | awk '{print $2}'`
termTitle="$termTitle : $size"
setTitle "$termTitle"
# read x
echo

# exit 0

# backup_dir=/data/staging$dvd_device
backup_dir=/data/movies

title=`dvdbackup -i $dvd_device -I 2>/dev/null | grep 'DVD-Video information of the DVD with title' | sed -e 's/.* title //'`

setTitle "$termTitle : $title"
if [ "$title" = "" -o "$title" = "DVD_VIDEO" -o -d $backup_dir/"$title" ] ; then
	echo 
	read -p "DVD Title '$title' already exists, or is stupid.  Please enter another name, or ENTER to overwrite with the current name " newtitle
	if [ "$newtitle" != "" ] ; then
		title=$newtitle
	fi
fi

setTitle "$termTitle : $title"

status=0
if [ "$title" = "" ] ; then
    echo "The disc name is still invalid.  Exiting."
    status=1
else
    echo "STARTING RIP OF '$title'"

    # Background progress indicator
    while [ true ] ; do
	sleep 30
	setTitle "$termTitle : `du -sh $backup_dir/"$title" | awk '{print $1}'` : $title"
    done &

    time dvdbackup -M -i $dvd_device -o $backup_dir -n "$title"
    chmod -R a+r $backup_dir/"$title"
    find $backup_dir/"$title" -type d -exec chmod a+x {} \;
    echo "DONE RIPPING '$title'"
fi

# Stop the background process indicator
kill %%

eject $dvd_device

setTitle "DONE $termTitle : $title"

echo "$title"
echo "Enter a new name, or just ENTER to quit"
read renameTitle
if [ "$renameTitle" != "" ] ; then
    mv $backup_dir/"$title" $backup_dir/"$renameTitle"
fi

exit $status
```

---

### Post by kpkeerthi on 2009-04-17
What happens when you run this script? Does it print anything? Can you post back the output.

The script seems to log something in /var/tmp/ripdvdsub.log. What do you have in there?

---

### Post by einnar on 2009-04-17
There is no output in that file at the point that the script stops.

Here's the output :
```

df: `sub': No such file or directory
df: no file systems processed


DVD Title '' already exists, or is stupid.  Please enter another name, or ENTER to overwrite with the current name Test
STARTING RIP OF 'Test'
Cannot open specified device sub - check your DVD device

real	0m0.004s
user	0m0.004s
sys	0m0.000s
chmod: cannot access `/home/einnar/Videos/Test': No such file or directory
find: /home/einnar/Videos/Test: No such file or directory
DONE RIPPING 'Test'
./ripdvd: line 73: 18203 Terminated              while [ true ]; do
    sleep 30; setTitle "$termTitle : `du -sh $backup_dir/"$title" | awk '{print $1}'` : $title";
done
eject: unable to find or open device for: `sub'


```

The pathing is different from my first post. I posted the unchanged script from the download. Before I ran it for output, I changed the paths to be correct. /home/einnar/Videos/ exists, and the script is supposed to create the "Test" subdirectory based on the movie name.

In the script, there is a line that says ```
dvdbackup -M -i $dvd_device -o $backup_dir -n "$title"
``` It works correctly if I manually put in pathing and title details.

The script has been given rights to run.

Thanks. :)

---

### Post by einnar on 2009-04-19
Bump!
:popcorn:

---

### Post by tidris on 2009-04-19
What command line are you using to run the script? It looks to me like you aren't passing the correct dvd device name when you run it.

---

### Post by einnar on 2009-04-19
I'm just running the script.

If fixing it involves passing it the correct device name, that's the sort of help I'm looking for.

It worked with previous versions of ubuntu, but now it doesn't. :(

The manual command that does work is this :

```
dvdbackup -M -n TITLE -i/media/cdrom0 -o/home/einnar/Videos 
```

TITLE being where I manually type the name of the movie.

I'm looking to get the full script working, though. It showed % done as part of the title, asked for a movie name if it wasn't part of the DVD name, etc...

There also used to be a way to set it up so that the script was automatically run if a DVD was put into the drive.

They beauty of it was that I could put a DVD in, it'd fire up, and I knew it was done when it ejected. I could see how far along it was at any point as well.

---

### Post by tidris on 2009-04-19
Your script is expecting the device name as the first argument when you run it. So, on a terminal window you would type

name_of_script_here    /media/cdrom0 [ENTER]

If you are just double-clicking the script's icon, then no arguments are being passed to it, and that is why it fails.

The command line above assumes the script is in the terminal's search path. If it isn't then you would need to specify the full path to the script.

---

### Post by einnar on 2009-04-19
Aaaahhh.. that makes sense..


So the reason it's not working is that it isn't being launched as it was previously, i.e. the change to the "Removable Drives and Media" tab being moved to the preferences screen of Nautilus?

Any way to get the script to be autorun on DVD insertion, then?
It used to be that I had the following in under "Run a script" for the Removable Drives and Media settings :

```
"/home/einnar/Videos/ripdvd %d"
```

Which makes sense when I look at it, as the %d must have been passing the CDROM info to the script, right? I just copied this all out of the original post on lifehacker and it worked. I never figured out exactly how...

Learning is gud...:D

---

### Post by einnar on 2009-04-19
Pure Genius.. :)  Thanks. 

I put in "/home/einnar/Videos/ripdvd /media/cdrom0" on the command line, and it's working fine. I kept thinking it was the script that had a problem, not something else.

Can't wait to see if there is a way to automate it like before. :D

---

### Post by tidris on 2009-04-19
> **einnar said:**
> Aaaahhh.. that makes sense..


So the reason it's not working is that it isn't being launched as it was previously, i.e. the change to the "Removable Drives and Media" tab being moved to the preferences screen of Nautilus?

Any way to get the script to be autorun on DVD insertion, then?
It used to be that I had the following in under "Run a script" for the Removable Drives and Media settings :

```
"/home/einnar/Videos/ripdvd %d"
```

Which makes sense when I look at it, as the %d must have been passing the CDROM info to the script, right? I just copied this all out of the original post on lifehacker and it worked. I never figured out exactly how...

Learning is gud...:D

You are right about all that. I think you can still automate it via the Media tab in the Nautilus preferences. One of the options in the menus there is "open with other application", and that brings a list of applications. Below the list there is a "use a custom command" triangle that I think is where you can type the code you listed above.

---

### Post by mc4man on 2009-04-19
> Can't wait to see if there is a way to automate it like before

I happen to use vobcopy thru a script to autorip from any dvd drive but the idea would be the same here.

In intrepid it would be very simple, in 'file management', DVD Video there is a drop down to insert a custom command.

In your case the command would be /path/to/script/scriptname
(**for auto run no need to specify device or mount point**.
As a test in intrepid works fine (worked from both drives), never seems to get volume label though, but after entering it, it runs as expected
> ]0;RIP /media/cdrom1 : 7.0G
]0;RIP /media/cdrom1 : 7.0G : 
DVD Title '' already exists, or is stupid.  Please enter another name, or ENTER to overwrite with the current name 300
]0;RIP /media/cdrom1 : 7.0G : 300STARTING RIP OF '300'
]0;RIP /media/cdrom1 : 7.0G : 335M : 300
.......


For hardy you'll need to create a .desktop, copy to ~/.local/share/applications and then add the .desktop to the appropriate line in ~/.local/share/applications/mimeapps.list

I could drop into hardy to ck. but goes something like this

In your home folder create an empty file and name it rip.desktop

Then in a terminal go 
```
gedit ~/rip.desktop
```

copy and paste this in
> [Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=
Name=
Comment=Autorip dvd with dvdbackup
NoDisplay=true
Icon=

For the Exec= add /path/to/script/scriptname

For example if loose in home folder and named ripdvd
Exec=./ripdvd

For name add anything you wish Ex.
Name=ripdvd

Then in terminal go 
 ```
cp ~/rip.desktop ~/.local/share/applications
```

Then go 
```
gedit ~/.local/share/applications/mimeapps.list
```

Find this line
> x-content/video-dvd=
and add ```
rip.desktop;
``` to the end (or beginning if you want to immediately set as default

Ex. my line, added rip3.desktop (your script)

> x-content/video-dvd=rip3.desktop;smplayer.desktop;mplayer-dvdnav.desktop;vlc9.desktop;

Then go Ctrl+Alt+backspace to restart x and register the mimetype

here's a thread that explains a bit more for hardy, handy if you don't have a mimetypes.list yet

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)


Note
I use a lot of scripts and to make life easy you can create a folder named bin in your home folder.
Then a simple command will add it to your path.
The advantage there is that any script or exec placed inside can be called just by it's name (either in a .desktop or from the terminal

So for example I named your script riptest and the Exec= is 
Exec=riptest

---

### Post by einnar on 2009-04-19
disregard this post.. didn't see the last reply. 

trying it.

---

