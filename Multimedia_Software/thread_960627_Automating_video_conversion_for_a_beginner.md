---
title: "Automating video conversion for a beginner"
date: 2008-10-27
forum: Multimedia Software
---

### Post by CityOflawrence on 2008-10-27
Hey guys, my job requires me to convert video from raw files ripped from DV tapes to mpegs. No problem. From there, the mpegs get used to make a DVD video and then a DVD is burnt, and the mpeg gets converted to a flash file that I send to the networking guy to upload to a server, or whatever it is he does with it. All of this I can do.

However, I want to figure out how to automate the process. I want to start easy, though. So my question is, how can I make it so I drop video files in a folder on my computer and then at a certain time- let's say midnight to ensure I've done everything I need to do that day -the computer system:
1) Converts the video to flash
2) Deletes the source file from the folder
3) After it runs out of files, shuts down

I use the command "ffmpeg -i sourcefile.mpg -ab 128 output.flv" to convert the video, which works really well, but I don't know how to delete the file from terminal, shut down the computer, or automate the process. Help would be appreciated.

My Workstation:
-Ubuntu Linux (Ubuntu Studio Release)- Hardy Heron

---

### Post by FakeOutdoorsman on 2008-10-27
Why do you convert from DV to mpeg to flv?  Why not DV to flv and DV to mpeg separately?  That way you don't go from one lossy format to another.  You can do this with cron and a bash script:
```
#!/bin/bash

# Convert all dv files to mpeg
find -iname "*dv" -exec ffmpeg -i {} -target dvd {}.mpg \;

# Convert all dv files to flv
find -iname "*dv" -exec ffmpeg -i {} -ab 128k {}.flv \;

# Remove dv files
rm *.dv

# Sleep for a bit before shutting down
sleep 3

# Shutdown computer
sudo shutdown -h now
```
I didn't test this script and I'm no programmer, but it should convert all .dv files that are in the same folder as the script and then shutdown.  You should add a check to see if it actually converted the files before deleting the dv files.  Save the above text to a file named "encode.sh" and give it executable permission:
```
chmod +x encode.sh
```
You need to edit your sudoers file so a certain user can execute the shutdown command without needing to add the password, otherwise your computer will sit there asking for the password when trying to shutdown:
```
sudo visudo
```
At the bottom of the file add:
```
angryscotsman     ALL=NOPASSWD:/sbin/shutdown
```
This will give passwordless shutdown ability to angryscotsman.  The last step is to make the script run when you want it to.  This is easy to do with a crontab and is explained here: [How-to for crontab]("http://ubuntuforums.org/showthread.php?t=102626").

---

### Post by CityOflawrence on 2008-10-29
Wow, that's pretty cool. Thanks. Now, how do I limit the search to just a particular folder? I don't want it converting all my files, just the ones I'm done editing and drop in a folder for the night. It would be /home/avuser/flvconversions, let's say.

Also, that was a good tip on the lossy format thing. Didn't even think of that.

---

### Post by FakeOutdoorsman on 2008-10-29
> **CityOflawrence said:**
> Wow, that's pretty cool. Thanks. Now, how do I limit the search to just a particular folder? I don't want it converting all my files, just the ones I'm done editing and drop in a folder for the night. It would be /home/avuser/flvconversions, let's say.

Also, that was a good tip on the lossy format thing. Didn't even think of that.

Here's a new version with some variables that you can change:
```
#!/bin/bash
# Encoding Script

# Location of source videos
sourcelocation="/home/avuser/flvconversions"
# Extension of source videos
sourceext="dv"

# Convert all dv files to mpeg
find ${sourcelocation} -iname "*${sourceext}" -exec ffmpeg -i {} -target dvd {}.mpg \;

# Convert all dv files to flv
find ${sourcelocation} -iname "*${sourceext}" -exec ffmpeg -i {} -ab 128k {}.flv \;

# Check to see if videos were encoded, then delete source vids and shutdown
if [ -e "${sourcelocation}/*.mpeg" ] && [ -e "${sourcelocation}/*.flv" ]; then
	# Delete videos	
	rm ${sourcelocation}/*.dv
	# Sleep for 10 seconds before shutting down
	sleep 10
	# Shutdown computer
	sudo shutdown -h now
else
	echo "Encoding FAILED"
fi

exit

```
The error checking part of the script sucks.  Basically it is just checking if **any** flv and mpeg files were made, and if so then it will delete all *.dv files and shutdown.  I didn't test this script, so I don't know if it will work at all.  You should head on over to #bash IRC and ask for a better way to do the check, or post the script in [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39").

---

### Post by mysoogal on 2009-05-24
> #!/bin/bash
# ffmpeg and mencoder script
# Grab thumb from avi, start encoding to ITU h264 using mencoder, ffmpeg is doing thumb processing

# Bash script for operating system Ubuntu 8.10
# packages used : FFMPEG, MENCODER ,MPLAYER ENCODING ENGINE
# VIDEO CODEC ITU H264 AUDIO MP3


# Written by FakeOutdoorsman and updated by mysoogal
# Attribution-Noncommercial 3.0 Unported
# [http://creativecommons.org/licenses/by-nc/3.0/deed.en](http://creativecommons.org/licenses/by-nc/3.0/deed.en)
# trackback [http://ubuntuforums.org/showthread.php?t=960627](http://ubuntuforums.org/showthread.php?t=960627)

# Location of source videos
sourcelocation="/var/www/uploads/"
# Extension of source videos
sourceext="mpeg"


# grab thumbs hehehe ! yahhoo hope this works!
find ${sourcelocation} -iname "*${sourceext}" -exec /usr/local/bin/ffmpeg -v 0 -y -i {} -vframes 1 -ss 200 -vcodec mjpeg -f rawvideo -s 200x130 -aspect 16:9 {}.jpg \;
# Check to see if videos were encoded, then delete source vids and shutdown
if [ -e "${sourcelocation}*.avi" ] && [ -e "${sourcelocation}/*.jpg" ]; then
	# Delete videos	
	rm ${sourcelocation}/*.avi
	# Sleep for 10 seconds before shutting down
	sleep 10
	# Shutdown computer
	# sudo shutdown -h now
else
	echo "Encoding FAILED"
fi


# Convert all video clips to ITU H264 OGM video container
find ${sourcelocation} -iname "*${sourceext}" -exec mencoder {} -o {}.ogm -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=300:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame \;


exit 


updated ffmpeg path so it gets jpg, when you run this script through crontab, it seems that ffmpeg needs to have full paths, and mencoder doesnt need it. weird

---

### Post by xzero1 on 2009-05-24
Will sudo somecommand work in a script without modification of the command properties?

---

### Post by FakeOutdoorsman on 2009-05-24
> **xzero1 said:**
> Will sudo somecommand work in a script without modification of the command properties?

I don't understand what you are asking.  Can you clarify your question?  Apologies if I am missing something simple.

---

### Post by mysoogal on 2009-05-24
> **xzero1 said:**
> Will sudo somecommand work in a script without modification of the command properties?

you mean if you use sudo to get bash script to start work ?

it seems to be working for me just asked me for password and i put my password and encoding started

```
yugo@ubuntu:~$ cd /home/yugo/Desktop
yugo@ubuntu:~/Desktop$ cd video
yugo@ubuntu:~/Desktop/video$ sudo bash h264
[sudo] password for yugo: 

```

---

### Post by xzero1 on 2009-05-24
No, what I mean is when the script executes sudo shutdown, there will be no one there to enter the password.

Edit:
Yes, you should edit the "sudoers" file. See this thread [http://ubuntuforums.org/archive/index.php/t-1121628.html](http://ubuntuforums.org/archive/index.php/t-1121628.html)

BTW, starting the script with sudo won't work and is not needed.

---

### Post by mysoogal on 2009-05-24
> **xzero1 said:**
> No, what I mean is when the script executes sudo shutdown, there will be no one there to enter the password. I know this can be modified to work, but I don't recall the specifics at this time.

oh i see,

im not sure i have to read more about it :KS

---

### Post by xzero1 on 2009-05-24
See my edited post.

---

### Post by mysoogal on 2009-05-24
> **xzero1 said:**
> See my edited post.


thanks I noticed ! :KS

back to figuring out more features to add maybe mysql the output to database and have php read from that database and display with vlc plugin ! 

i'm getting closer to a video ubuntu sharing bash script lol

---

### Post by FakeOutdoorsman on 2009-05-24
> **mysoogal said:**
> hope you don't mind but i taken a liking to this script you wrote and updated it to my needs

grabs image,convert to h264 and thats it lol


```
#!/bin/bash
# ffmpeg and mencoder script
# Grab thumb from avi, start encoding to ITU h264 using mencoder, ffmpeg is doing thumb processing

# Bash script for operating system Ubuntu 8.10 
# packages used : FFMPEG, MENCODER ,MPLAYER ENCODING ENGINE
# VIDEO CODEC ITU H264 AUDIO MP3


# Written by FakeOutdoorsman and updated by mysoogal
# Attribution-Noncommercial 3.0 Unported
# http://creativecommons.org/licenses/by-nc/3.0/deed.en
# trackback http://ubuntuforums.org/showthread.php?t=960627

# Location of source videos READ this !!! add your user name !
sourcelocation="/home/ your user name goes here /Videos/"
# Extension of source videos
sourceext="avi"

# grab thumbs hehehe ! yahhoo hope this works!
find ${sourcelocation} -iname "*${sourceext}" -exec ffmpeg -v 0 -y -i {} -vframes 1 -ss 90 -vcodec mjpeg -f rawvideo -s 286x160 -aspect 16:9 {}.jpg \;
[color=#FF0000]# Check to see if videos were encoded, then delete source vids and shutdown
if [ -e "${sourcelocation}/*.avi" ] && [ -e "${sourcelocation}/*.jpg" ]; then
	# Delete videos	
	rm ${sourcelocation}/*.dv
	# Sleep for 10 seconds before shutting down
	sleep 10
	# Shutdown computer
	# sudo shutdown -h now
else
	echo "Encoding FAILED"
fi[/color]


# Convert all video clips to ITU H264 OGM video container
find ${sourcelocation} -iname "*${sourceext}" -exec mencoder {} -o {}.ogm -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=300:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame \;



exit
```

You can remove the text I colored red because you are not using .dv files and you commented out the shutdown command that the original poster wanted.

---

### Post by xzero1 on 2009-05-24
You have reminded me to post my own recording script. You may be interested in some of the code. See my post [http://ubuntuforums.org/showthread.php?t=1169204](http://ubuntuforums.org/showthread.php?t=1169204)

---

### Post by mysoogal on 2009-05-24
it seems that cron job only encoding one video. and doesn't get jpg :O and misses the other videos. I've figured to test it with 15 mints which I did, so the same thing happens encodes the video everything OK but no jpg

I've set the bash to ```
chmod u+x h264
```

and set the cron like this 

crontab - e

```
*/1 * * * * /usr/bin/h264
```

I'm wondering is this because I moved the thumb code above the encoding code ? :o

I also uncommented Delete , it also doesn't seem to be deleting the .avi source file
.


sorry that part I like it to stay there, since its a little different script that deals with avi not dv like the original I've changed that dv into avi instead. hopefully things should run smooth :KS but if its not working. it will be removed and replaced with something that works.

so far CronTab is not working fully with this bash script. maybe due to permission issues. will ask some more on irc



/ i see, maybe i should run the ffmpeg and mencoder with SUDOERS instead, maybe this is why script only encodes 1 video and doesnt get jpg

---

### Post by xzero1 on 2009-05-24
Using exec causes problems in some scripts you might check that.

---

### Post by mysoogal on 2009-05-29
> **xzero1 said:**
> Using exec causes problems in some scripts you might check that.

> -exec /usr/local/bin/ffmpeg

fixed it it seems.

found this perfect crontab GUI called  

> sudo Install Gnome-schedule 

it runs very well with this script just make new recurrent with every hour and script path.

> /usr/bin/scriptname 

it encoded every video and grabbed thumbs. now have to figure out why its not deleting the input file after encoding finished


next features maybe move the encoded videos to somewhere else and input that information to sql and a simple php file to view the videos. :p

---

### Post by sco` on 2012-03-01
Hi, 

i didnt want all the videos downloaded from say youtube using either "get_flash_videos" or "minitube" split into all those pesky parts... 

(i think there are gui based automated ways of doing this, but wheres the fun in that :s)

having read part of the ffmpeg man [http://www.ffmpeg.org/faq.html#How-can-I-join-video-files_003f](http://www.ffmpeg.org/faq.html#How-can-I-join-video-files_003f) i also didnt want to have to do run the commands...

ffmpeg -i input1.avi -same_quant intermediate1.mpg ffmpeg -i input2.avi -same_quant intermediate2.mpg cat intermediate1.mpg intermediate2.mpg > intermediate_all.mpg ffmpeg -i intermediate_all.mpg -same_quant output.avi

(if there are a lot of files, id be waiting around a long time... (damb not just being able to cat > *.mp4 files) so I found this thread!)

here is my edited version of whats been done here.... 
as you can see i have very, very limited knowledge of bash scripting and almost as little with knowing the tools like grep, cat, rm! lol  

```
 #!/bin/bash
# Location of source videos
sourcelocation="/home/me/Videos/convo"
# Extension of source videos
sourceext="mp4"
# Extention of temp converted files
conversionext="mpg"

# Convert all video clips to mpg video container (so can be joined to one file)
find ${sourcelocation} -iname "*.${sourceext}" -exec /usr/local/bin/ffmpeg -i {} -same_quant {}.mpg \;

# join to one file
find ${sourcelocation} -iname "*.mpg" | cat *.mpg > $file.mpg

# converting back from mpg to mp4
/usr/local/bin/ffmpeg -i ${sourcelocation}/$file.mpg -same_quant $file.mp4

# remove temp mpg containers created for joining files together
grep "*.$conversionext" $sourcelocation | rm *.$conversionext 
```My question here appart from the obvious "How can i make this better!?"

where i need to "join to one file" 
find ${sourcelocation} -iname "*.mpg" | cat *.mpg > $file.mpg
what other commands can i use to name the newly created $file.mpg

sed?  

i would like to use the original filename minus the part_1 part_2 etc.. so that i could grep and move that to another dir at the end, so that all the contents of the convo folder can be del after....

an obvious limitation to this script is that the folder can contain only the one film for example. otherwise it would join lots of different shows/films together. Again, if i knew a good way - rather than just using wildcards - i think that would solve it.

Thanks

---

