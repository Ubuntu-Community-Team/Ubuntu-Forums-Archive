---
title: "Lost Playback Ability On One Channel"
date: 2009-02-02
forum: Mythbuntu
---

### Post by raymacke on 2009-02-02
My Ubuntu 8.04 system has been running flawlessly. I use Over The Air signals and capture with 3 tuners. On 1/28/09 all channels recorded fine but on 1/29 I developed a problem playing back recordings from ONE channel - KMOV - CBS channel 4 in St Louis Mo.  Programing records but will not play back.  I get a black screen and no sound. Plus the hard drive light stays on constantly not flickering as when normal play back and the system is more or less hung. Usually hitting the ESC keey will clear it after a few minutes and drop back to the main menu. Does not make any difference if the programing is or isn't high def - neither will play back in Ubuntu.

 All other channels record and playback perfectly. I can exit Myth and use VLC Media player and the Channel 4 files will play fine. Also, I can watch this channel as Live TV with no problem. Plus, when looking at the Media Library the thumbnail preview of the recordings will play. Just can't playback the recording in Ubuntu. I updated to 8.10 but no change in the problem.

Any thoughts anyone? Could sure use some help.

---

### Post by klc5555 on 2009-02-02
> **raymacke said:**
> My Ubuntu 8.04 system has been running flawlessly. I use Over The Air signals and capture with 3 tuners. On 1/28/09 all channels recorded fine but on 1/29 I developed a problem playing back recordings from ONE channel - KMOV - CBS channel 4 in St Louis Mo.  Programing records but will not play back.  I get a black screen and no sound. Plus the hard drive light stays on constantly not flickering as when normal play back and the system is more or less hung. Usually hitting the ESC keey will clear it after a few minutes and drop back to the main menu. Does not make any difference if the programing is or isn't high def - neither will play back in Ubuntu.

 All other channels record and playback perfectly. I can exit Myth and use VLC Media player and the Channel 4 files will play fine. Also, I can watch this channel as Live TV with no problem. Plus, when looking at the Media Library the thumbnail preview of the recordings will play. Just can't playback the recording in Ubuntu. I updated to 8.10 but no change in the problem.

Any thoughts anyone? Could sure use some help.

I have had the same issue for about 4 months on one (and only one) high-def QAM channel. (The local ABC in my case.) Recordings from this channel will not play on any of my myth frontends.

I suspect the problem revolves around how their sound is broadcast, but I haven't had the time to really try to debug the issue.

But what I did discover in my case was that with recordings from this station a simple lossless transcode fixes it, i.e. 

mythtranscode --mpeg2 -c -s 

And the resulting *.mpg.tmp file, when moved to *.mpg plays fine. So I set automated the neccessary steps in a script that runs as a postprocessing user job for just this channel, and I keep in mind that recordings from this channel won't be viewable until about 15 minutes after they finish recording. Good enough for the time being.

Hope this helps. :)

---

### Post by raymacke on 2009-02-03
I really appreciate the information. I am not too Myth savvy as my son set this up for me and trying to get him to take time to help is always a problem. I understand "parts" of the software but have never messed with transcoding. But I will sure try to sort through it as having to use one of the media players is a pain!

---

### Post by raymacke on 2009-02-03
Is there an online tutorial to walk me through this process?

---

### Post by klc5555 on 2009-02-04
> **raymacke said:**
> Is there an online tutorial to walk me through this process?

I don't think there's a tutorial for this process. The wiki has guides for bits and pieces of it. The page for the mythtranscode command itself is here: [http://www.mythtv.org/wiki/Mythtranscode](http://www.mythtv.org/wiki/Mythtranscode)

Your problem is in two main parts. The first is to see whether the difficulty with the recordings from the one channel is of the simple nature that just doing a lossless transcode can fix them. If it can, the second part would be to automate the process when recording from that channel. You'll need to be able to use the Linux command line some.

1) Find the actual recording file for an affected recording to test. All myth recordings files (in the direcories in your Default Storage Group) have the following structure: xxxx_yyyymmddtttttt.mpg The first 4 digits are mythtv's own little code for the channel of the recording, then an underscore, then the four digit year, two digit month, two digit day, and six digit time (down to the second) that the recording started. 
So that if I happen to have started a recording on my HD Fox affiliate channel, which myth tags internally as channel "1251", of, say, "House" on Monday Feb. 2 at 8PM (and recording started at exactly 8PM), I would expect to find a recorded file named 1251_20090202200000.mpg (8PM becomes 20:00:00 in 24 hr. time down to the second)

So to find one of your recording files, look to see exactly when one of your affected recordings started. Let's say Jan 21 at 1 AM. From a command line change directories into the directory your recordings are stored in. 

cd  /<the_path_you_have_listed_to_your_storage_directories>

(If there are multiple directories in your "default storage group", you may need to search them all. In this directory, search for the file from the information you have:  

ls -l *200901210100* 

(that is -l "ell" for "long", with asterisks for "wildcards" in the search) and you should get 2 hits: a big file ending in .mpg (or .nuv) which is the recording that started at that time, and a smaller file ending in .png, which is the thumbnail presentation of that recording.

2)Now you try to fix this recording. From this same prompt, run the following mythtranscode command on the recording file you found. Let's say the full name of this file turned out to be 1051_20090121010000.mpg

mythtranscode --mpeg2 --showprogress -c 1051 -s 20090121010000

and let it chug away. (-c marks the channel, and -s marks the full start time.) Hopefully mythtranscode will make it to the end of the file without erroring out. You will now have two files: your original recording, which has been left exactly as it was, and a second file, which in this example will be named 1051_20090121010000.mpg.tmp This .tmp file is the (hopefully) fixed recording.

3)Now we move the fixed recording to where the database can find it. First we save the original, renaming it as an ".old" file:

mv 1051_20090121010000.mpg  1051_20090121010000.mpg.old

And now we turn the .tmp file into the main recording:

mv 1051_20090121010000.mpg.tmp  1051_20090121010000.mpg

And finally, we will want to make the owner of this new recording "mythtv" (and not you) so that it eventually can be expired or deleted from the Mythfrontend:

sudo chown mythtv 1051_20090121010000.mpg 

4)Now go into Mythfrontend and see if Myth can play the thing. If it can, the surgery was a success, and we can then worry about automating the process. If it still doesn't play, then we have a more serious or different problem.

Good luck! :)

---

### Post by raymacke on 2009-02-05
Victory!!! It worked!  Played just fine in Mythtv. Commercial Skip even worked. Can't tell you how much I appreciate this. NEVER would have gotten there on my own.  I messed for several hours last night and got nowhere.

Now, if I can just impose on you a little more by helping me with the automation process!

Again, I really appreciate this!

---

### Post by klc5555 on 2009-02-05
> **raymacke said:**
> Victory!!! It worked!  Played just fine in Mythtv. Commercial Skip even worked. Can't tell you how much I appreciate this. NEVER would have gotten there on my own.  I messed for several hours last night and got nowhere.

Now, if I can just impose on you a little more by helping me with the automation process!

Again, I really appreciate this!

Now, if I can just impose on you a little more by helping me with the automation process!

Again, I really appreciate this![/QUOTE]

Glad it worked! :D

There may be several ways to automate this business, but I use a simple script set up as a user job.

On the mythtv wiki there is a script originally written to autogenerate cutlists and cut recordings. This was stripped down by Ian Barton on his website 
[http://www.ian-barton.com/MythTV/HomePage](http://www.ian-barton.com/MythTV/HomePage)
to help in the editing process for dvb recordings. A small piece of this script with edits works for our purpose:

-------------------------

#!/bin/sh
VIDEODIR=$1
FILENAME=$2
CHANID=$3
STARTTIME=$4

# Sanity checking, to make sure everything is in order.
if [ -z "$VIDEODIR" -o -z "$FILENAME" ]; then
        echo "Usage: $0 <VideoDirectory> <FileName>"
        exit 5
fi
if [ ! -f "$VIDEODIR/$FILENAME" ]; then
        echo "File does not exist: $VIDEODIR/$FILENAME"
        exit 6
fi

# Use --mpeg2 to fix audio sync problems.
# Note that mythtranscode seems to ignore --honorcutlist when using -i
# so we use the chanid and start time instead
# This further edit of the script also eliminates --honorcutlist

mythtranscode  --mpeg2 -c $CHANID -s $STARTTIME -o $VIDEODIR/$FILENAME.tmp

ERROR=$?

if [ $ERROR -ne 0 ]; then
        echo "Transcoding failed for ${FILENAME} with error $ERROR"
        exit $ERROR
fi

# The original file is saved with a .old prefix.
# You probably need a cron job to remove these files every few days.
#  If you don't wish to save the original file, moving the file to *.old may be commented out

mv $VIDEODIR/$FILENAME $VIDEODIR/$FILENAME.old
mv $VIDEODIR/$FILENAME.tmp $VIDEODIR/$FILENAME


# The rest of the script is not necessary here, and is removed.

fi

--------------------------------

If you make a file of such a script with your favorite editor --say, copy and pasting it into a kedit screen or similar, the script can in turn be made a user job.

Name the file as, say, "hdfix". Save it into your home directory. Check the file to make sure that word wrap in your editor has not zapped you by wrapping any of the longer comments (the lines starting "#") into 2 lines, where the command interpreter will try to run the line leftover as a command.

If the file looks good, make it executable:

chmod +x hdfix

Now, as it stands, the script could be run manually from the command line by "hdfix" followed in order by the four pieces of information its variables are asking for, e.g.:

hdfix /var/lib/mythtv/recordings  1051_20081225040000.mpg  1051  20081225040000

And if set as a user job, it will work on all new recordings. But you only want one channel operated on. So...

Make sure the first user job is enabled on your backend. The wiki page on user jobs is here: 
[http://www.mythtv.org/wiki/User_Jobs](http://www.mythtv.org/wiki/User_Jobs)
In the General page in the backend setup that pertains to user jobs, call the job whatever you want. Then set up the command on "User Job #1 Command: ". This normally would be set up as follows:

/<the full path to your script>/hdfix %DIR% %FILE% %CHANID% %STARTTIME%

The position of the 4 variables in your user job command line  correspond in order to the 4 variable positions at the start of the script. But you actually want only one channel operated on. So in your case, the job command line would be set up as:

/<the full path to your script>/hdfix %DIR% %FILE% the_actual_4_digit_channel_ID  %STARTTIME%

where you put the actual 4 digits of myth's ID of the fatal channel into the 3rd position where %CHANID% used to be, and where your script expects it to be.

Once the user job command line is set up and the backend restarted, new recordings should end up in the queue for processing; new recordings on the fatal channel should actually be processed and be ready to view 15-30 minutes or so after recording completes. On older recordings on the fatal channel, in View Recordings, for a particular recording, right-clicking should pull up a menu that includes "Job Options". One option now listed will be "Run User Job #1". Which you can run from that menu.

The script is set up to save old recordings. Assuming everything is working correctly, you'll need to go into your recording directories every so often and delete the *.old files. Eventually if you are satisfied everything is operating correctly, you may not wish to save the original file at all when processing is complete. A single "#" placed at the head of the line that mv's the original file to .old will do this:

  # mv $VIDEODIR/$FILENAME $VIDEODIR/$FILENAME.old

and the original file will be overwritten by the fixed *.tmp file when the fixed file becomes the .mpg

Good luck! :)

---

### Post by raymacke on 2009-02-09
Again - It worked! It took me a while to sort through this. Not that your directions weren't on the money but rather because of my lack of knowledge for completing even basic task in Linux. I finally had to bribe my son into helping but still learned a lot along the way.

Actually I got close on my own. Since I didn't know how to download Kedit I decided the easiest way for me to create the file to run the script was to copy paste the text in WINDOWS and use Notepad to make the file. I then pasted it into a Myth folder which I can access over my network. Sounded good and the file looked good but it wouldn't run. The log error said it could not find the file even though it was there. My son downloaded Kedit and created the file within Linux and that fixed the problem.

Again, I really thank you for the help. I was afraid I was going to be stuck using a media player to watch the recordings from the one channel. But now this solves the problem.

---

### Post by klc5555 on 2009-04-04
> **raymacke said:**
> Again - It worked! It took me a while to sort through this. Not that your directions weren't on the money but rather because of my lack of knowledge for completing even basic task in Linux. I finally had to bribe my son into helping but still learned a lot along the way.

Actually I got close on my own. Since I didn't know how to download Kedit I decided the easiest way for me to create the file to run the script was to copy paste the text in WINDOWS and use Notepad to make the file. I then pasted it into a Myth folder which I can access over my network. Sounded good and the file looked good but it wouldn't run. The log error said it could not find the file even though it was there. My son downloaded Kedit and created the file within Linux and that fixed the problem.

Again, I really thank you for the help. I was afraid I was going to be stuck using a media player to watch the recordings from the one channel. But now this solves the problem.

As it happens, a poster on the Mythtv list this has apparently tracked down the source of this problem.

Not all HD broadcasts in all areas use the same resolution. Some playback profiles in the Mythfrontend (e.g. "CPU+") use XvMC for playback for some resolutions, but not others. If your station broadcasts HD at a resolution that your playback profile uses XvMC for, but XvMC is not enabled on your machine for whatever reason, you end up with blackscreen and high disk usage when you try to play back a recording from this station, until you transcode it.

If your machine doesn't do XvMC, changing the playback profile (in setup-tv settings-playback) to something that doesn't require XvMC for any resolution, e.g. the "Slim" profile, fixes it. Simple as that. Aargh! these things make me feel stupid.  :-x

---

