---
title: "1 step tool for burning films to DVD (alpha version)"
date: 2007-03-16
forum: Multimedia &amp; Video
---

### Post by CookieNinja on 2007-03-16
I just wrote this script tonight, complete with a basic GUI and thought I would share it with people. This is a very rough draft of a script written to suit me. However, if there's enough interest then I would like to solve the obvious failings listed below and package it as a .deb for normal people to use.

ps. don't be too harsh. I am no coder and this has been created in a rush to suit my needs ... I just think that if I was to polish it off then other people would like it as much as I do.

dependencies are as follows:

mencoder
dvdauthor
growisofs
zenity
video codecs for mplayer, so that mencoder can do the format conversion.


*note this bit has been edited to update the original script, posted in a later post, used to do the job.* I will ALWAYS have my latest script in the 1st post so that nobody uses an old one by accident.

OK. I have simplified things a lot here. This is an update to the original script to make it simpler to install.

Just copy and paste the following into an empty txt file called "makedvd.sh" and place in this location. Don't forget to make sure it is executable.

~/.gnome2/nautilus-scripts/

That's it, job done. I'm learning more about shell scripting as I go along here, so if I have made a mistake or things too complicated, then let me know.

The final version, what I shall call my 1.0 "release" will have this work as it does in the screenshot above, and you will also be able to install it as a .deb package. I'm reasonably sure that I know enough to do that. It will also log errors so that I can help people with problems.

```

#!/bin/bash

# Simple script to burn films to DVD.

# This checks for and creates the required folders for the script if they don't exist.

if [ ! -d /home/$USER/.makedvd/ ]
then
	mkdir /home/$USER/.makedvd
fi

if [ ! -d /home/$USER/.makedvd/tmp ]
then
	mkdir /home/$USER/.makedvd/tmp
fi

# This creates a simple xml file, needed to create a dvd image, if it doesn't already exist.
# It might be worth creating a new one all the time, just to make sure it's as it should be.
# Eventually, I want a more complex one made on the fly, anyway.

if [ ! -r /home/$USER/.makedvd/dvd.xml ]
then
echo "<dvdauthor>
  <vmgm />
    <titleset>
      <titles>
        <pgc>
          <vob file=\"/home/"$USER"/.makedvd/tmp/film.mpg\" />
        </pgc>
      </titles>
    </titleset>
</dvdauthor>" > /home/$USER/.makedvd/dvd.xml
fi

# notice to say dvd burning is about to start. I may get rid of this if I implement some sort of progress bar.

 zenity --info --text="Click OK to start burning a DVD"

# convert film to mpg so it can be used to make a DVD
if mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:576,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:aspect=16/9:acodec=ac3:abitrate=192 -ofps 25 -o ~/.makedvd/tmp/film.mpg "$*" 2>> /home/$USER/.makedvd/error.log
then
        # make a DVD image using the mpg copy of the film.
        if dvdauthor -o ~/.makedvd/tmp/dvd -x ~/.makedvd/dvd.xml 2>> /home/$USER/.makedvd/error.log
        then
                # Burn DVD image to a DVD disc.
                if growisofs -dvd-compat -speed=2 -Z /dev/dvdrw -dvd-video ~/.makedvd/tmp/dvd 2>> /home/$USER/.makedvd/error.log
                then
                        rm -rf ~/.makedvd/tmp/dvd
                        rm ~/.makedvd/tmp/film.mpg
                        zenity --info --text="DVD has been successfully created"
                else
	                rm -rf ~/.makedvd/tmp/dvd
                        rm ~/.makedvd/tmp/film.mpg
                        zenity --error --text="attempt to burn to disc failed"
                fi
        else
		rm -rf ~/.makedvd/tmp/dvd
                rm ~/.makedvd/tmp/film.mpg
                zenity --error --text="failed to create a dvd image"
        fi
else
	rm -rf ~/.makedvd/tmp/dvd
        rm ~/.makedvd/tmp/film.mpg
        zenity --error --text="failed to convert avi to mpeg"

fi

```

---

### Post by mgmiller on 2007-03-24
This is exactly the kind of video support we need.  Makes it almost as easy to make a DVD that will play on  a set top player as it is to burn a CD.  When you say wide screen format, what aspect ratio are you using?  It would be great if it would be full screen on a wide screen TV, with no black bars on the top and bottom.   Another possible tweak would be support for multiple files so if you had say, 5 .avi's, they would create a simple menu that lets you pick which one to play.  Nothing fancy (yet), no graphics or sound, just a list you can click wilth your DVD player controller.

---

### Post by CookieNinja on 2007-03-25
> **mgmiller said:**
> This is exactly the kind of video support we need.  Makes it almost as easy to make a DVD that will play on  a set top player as it is to burn a CD.  When you say wide screen format, what aspect ratio are you using?  It would be great if it would be full screen on a wide screen TV, with no black bars on the top and bottom.   Another possible tweak would be support for multiple files so if you had say, 5 .avi's, they would create a simple menu that lets you pick which one to play.  Nothing fancy (yet), no graphics or sound, just a list you can click wilth your DVD player controller.

The aspect ratio is set to 16:9, so no black bars in sight anywhere.

There is a GUI program called DeVeDe that lets you work with menus and multiple video files. My only reason for working on this is so that the girlfriend can simply put in a blank dvd, right-click on a video file, choose "makedvd.sh" and wait for the job to be done.

Forthcoming changes for the next version are:

I know how to put a sort-of progress bar on each step the burning process now. It doesn't tell you the % progress, alas, it just produces a an animated bar to show something is going on. This seems to be a limitation of the program used to add GUIs to a shell script, unfortunately.

An icon appears in the systray when the job is done.

The temp files are stored in a standard, hidden, location instead of /dvd-temp. The /dvd-temp folder is just a spare partition I use exclusively for burning DVDs. The reason being that, because I have space set aside, I can *always* burn a disc, even if every other partition is 100% full.

Turning this all into a single script/file.

Have an installer script too, so that anyone can use it.


After that, the still to do list is:

Making a config/preferences type program to support this script. I don't want to build it into the script, because aside from trying to stick to the "KISS" principle, I think that the settings will be something that people fiddle with once and then leave alone.

Create a better dvd.xml file automatically.

Handle >1 video file.

I also want to do some decent error logging as soon as possible, too. It's not a priority right now, because it almost always works for me, but I do want to get it done as soon as possible.

I'd also like to be able to detect whether or not a codec/format is supported or not. That's going to take a lot more work, for me, so it's on the back burner.


Most of all, though, as much encouragement as possible would be nice :-) I would like to take this beyond a shell script into a "proper" program that integrates itself fully into the Gnome desktop.

---

### Post by mgmiller on 2007-03-25
> There is a GUI program called DeVeDe that lets you work with menus and multiple video files.

Very useful, thank you.  
Keep up the good work, your list of things to do sounds right on the money.

---

### Post by CookieNinja on 2007-04-08
I'm still working on this, but I have had an unexpected development that I didn't want to keep from myself.

The picture attached shows that I can now make nautilus display a "burn to dvd" option directly in the context menu when you right click on a movie file. Currently I have only made it do that when it's an avi file, but when I am done I'll change things so it will appear for any movie file extension that I am aware of instead.

The only thing I'll need to do after that is find out how I can make it installable as a .deb file. I know how to do that if it is to appear in the scripts folder as I originally planned but not when I use this new system.

What is this new system ? It's a tool called "nautilus actions", which allowed me to do this. If you want to add your own menu item to the context menu when you right click on a file then this is the tool for you!!!

---

### Post by lime4x4 on 2007-04-08
nice little app.works well in feisty..

---

### Post by 22.glenroy on 2007-04-21
Think I followed your instructions but just keep getting "failed to convert avi to mpeg"
error message.

---

### Post by CookieNinja on 2007-04-29
> **22.glenroy said:**
> Think I followed your instructions but just keep getting "failed to convert avi to mpeg"
error message.

OK. My 1st question is whether or not you can play the video file on the computer. My 1st concern is that the problem is that the codec required for either mpeg or the avi is not available. Also, I believe mencoder doesn't use the same codecs that gstreamer (gnome/ubuntu's audio/video framework) does. That means that being able to play it in totem doesn't mean you have the codecs that mencoder needs. I think you need the codecs that mplayer/xine uses to play videos.

I'll try to help as best I can, but I think my main concern is to produce a version that logs the output including errors. That way I can just ask for that output file and work out what is going wrong from there.

Sorry I can't be more useful than that right now.

---

### Post by CookieNinja on 2007-04-29
> **22.glenroy said:**
> Think I followed your instructions but just keep getting "failed to convert avi to mpeg"
error message.

Actually I have found another cause for that kind of problem, which will be fixed in the version I am working on. The script doesn't like spaces in the arguments passed to it. I think this will fix it, but I haven't tested it on the old script. It's sorted on the new one for sure, though.

See this bit of the script:

/dvd-image/dvd-tmp/film.mpg $1

replace

$1

with

"$*"

That's including the quotation marks.

---

### Post by CookieNinja on 2007-04-29
The script has been updated and the 1st post in this thread has been updated to reflect that. See it now, it is an awful lot better than the original, although it still has work that needs to be done to make it better.

I am always going to edit the 1st post to have the latest script, so that no-one gets the old one and everyone is up to date.

I am happy to get suggestions on making it better, too.

---

### Post by CookieNinja on 2007-05-06
I've made more change to it now, and fixed a stupid bug in it :-( I've not had to use this since i wrote it, for various reasons, so I've not spotted my silly mistakes!

It now clears out the tmp folder in ~/.makedvd/tmp after each attempt at making a DVD. That was my stupid mistake, but it's been sorted now.

The feature I was testing when I found that, though, was logging errors & warning messages to ~/.makedvd/error.log  so that people can post or PM me those to show me what is going wrong.

That file is going to keep on getting bigger as DVDs get burnt, though, so my next step has to be to  check on the size of the file, archive and then delete it when it gets beyond a certain size. I'll limit it to one log file and one archive file though.

Alas I've still not had time to turn this into a .deb to make it installable and also have a nice icon'd option in the context menu when you right click. I will get there, though! I can do it all manually, it's just packaging it into a .deb.

---

