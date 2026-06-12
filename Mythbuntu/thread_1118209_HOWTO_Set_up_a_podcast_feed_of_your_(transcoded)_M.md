---
title: "HOWTO: Set up a podcast feed of your (transcoded) MythTV recordings"
date: 2009-04-06
forum: Mythbuntu
---

### Post by Medieval Cow on 2009-04-06
So I have no idea if this is the kind of thing that's going to interest anyone else, but I'm really happy to have it, so hopefully someone else can get some use out of it. Right now I have my Mythbuntu box set up so that after it records a program it transcodes it to an iPod/iPhone friendly format stripping out the commercials as it does so, then updates a podcast feed with that recording. The recording can then be downloaded directly into iTunes automagically on my laptop, or I can even download it directly to my iPhone using the awesome [RSS Player]("http://rssplayer.blogspot.com") iPhone app. Here's how I did it.

**Step 1**


 Download the attached zip file and unzip the mythipod.sh and mythipodcom.sh scripts into your /usr/local/bin directory. These are modified versions of [these instructions]("http://www.mythtv.org/wiki/Streaming_to_iPod_touch_or_iPhone#Transcoding_and_Scripts"). The mythipodcom.sh one specifically is set up so it will automatically remove the commercials. There are other methods out there to transcode your recordings, but it's important to use one of these so that the file name turns out correctly. Set those scripts up in your /usr/local/bin directory, then set a job in MythTV to run “/usr/local/bin/mythipod.sh %FILE% %DIRECTORY%” (without the quotes) and another job substituting mythipodcom.sh. You may need to run ```
sudo chmod 755 mythipod*.sh
``` on the files to get it to work. Any recordings you set one of these jobs up on will then automatically be transcoded to iPod format after the recording finishes. If you use mythipod, it will just transcode it to iPod format. If you use the mythipodcom instead, the commercials will be cut out as well.
 

 **Step 2**
 

 Next, unzip the mythexpire.pl script and add that to the /usr/local/bin directory as well (again, chmodding as necessary). [Set up a cron job]("https://help.ubuntu.com/community/CronHowto") to run that as often as you'd like. Mine runs every hour. That script deletes the transcoded recordings when you delete the original recording, keeping the directory clean and uncluttered. It also updates the podcast feed to remove the deleted items as well.

**Step 3**

Run ```
sudo ln -s /var/lib/mythtv/recordings /var/www/recordings
``` This creates a symlink to your recordings directory so that it can be accessible via the web.
 

 **Step 4.**
 

 Unzip the feed.pl script, again to /usr/local/bin (and again chmodding as necessary). Open it up in a text editor and edit it where indicated at the top of the script. Set that script up as a job in MythTV as well (/usr/local/bin/feed.pl). Make sure you set it as a job number *after* the mythipod and mythipodcom jobs so that it runs after those complete. Now select that job as well when you set up a new recording and the feed will automatically be updated after the transcoding finishes. Note that if you use the script that cuts out commercials, you'll need to make sure you select the “flag commercial breaks” job to run on your new recordings as well.
  

 **Step 5.**
 

  Make sure you can access your MythTV box from the Internet. If you've already setup MythWeb, you should be set here. If you go to [http://The.IP.OfYour.MythbuntuBox/recordings/feed.xml](http://The.IP.OfYour.MythbuntuBox/recordings/feed.xml), you should then be linked directly to the RSS feed of your recordings, assuming you've used a recording that ran the feed.pl script. Assuming that's displaying correctly, you can now paste that address into iTunes, RSS Player, or another podcatcher application and your recordings should be downloaded there automagically when they're finished


And that's all there is to it. For extra credit, set up a [dyndns.com]("http://www.dyndns.com/") redirect to your server so you don't have to remember your IP address, and to handle any changes if your ISP doesn't provide you with a static IP. And please do post if anyone tries this out!

[SIZE=1]7/29 Edited to update the file. Fixed a small bug that would display the wrong time in the feed for recordings starting between midnight and 12:09 AM.[/SIZE]

---

### Post by Caps18 on 2009-04-07
This is really cool, and I may have to look into getting my parents a Mythbuntu box as well.  I guess my question is, could I setup my Mythbuntu box in Ohio to download shows from a Mythbuntu computer in Michigan?  I wouldn't mind watching the local news sometimes (the news girl is hot).

There is also the implication that there could be a worldwide Mythbuntu network, and if there was a show in England, Canada, or Australia (or where ever else) that I don't have access to, then this could enable it.  But, I'm sure there could be some copyright issues that would have to be dealt with.

---

### Post by Medieval Cow on 2009-04-07
Thanks! You can absolutely set it up to download them from Michigan to Ohio or anywhere else that has Internet access. If I had gotten this set up earlier, I'd have been able to shoot the link for the feed to my brother, who's been teaching English over in Japan for the last year and a half. Since he's coming home next week, there isn't much point now, though. Oh well. As far as it going to another Mythbuntu box? Well you can install a podcatcher on the machine, and if you set the download directory to be your videos directory, you'd be in business.

Yeah, I'm sure there would be copyright issues with publishing your feed for anyone to access over the Internet, especially if you're cutting out the commercials. This is definitely more of a personal thing I'm aiming for. I think BitTorrent is still the protocol of choice for getting content that hasn't been released locally. Not that I encourage that kind of thing, of course. ;)

---

### Post by minirx7 on 2009-04-15
Thank you so much..

I am going to give this a shot.

I am having SO MANY problems trying to get mythexport to work.  Just a question about RSS Player.  Does it use the native IPOD player?  In other words you hit play, it will see output the video through video output cable right (like youtube)




> **Medieval Cow said:**
> Thanks! You can absolutely set it up to download them from Michigan to Ohio or anywhere else that has Internet access. If I had gotten this set up earlier, I'd have been able to shoot the link for the feed to my brother, who's been teaching English over in Japan for the last year and a half. Since he's coming home next week, there isn't much point now, though. Oh well. As far as it going to another Mythbuntu box? Well you can install a podcatcher on the machine, and if you set the download directory to be your videos directory, you'd be in business.

Yeah, I'm sure there would be copyright issues with publishing your feed for anyone to access over the Internet, especially if you're cutting out the commercials. This is definitely more of a personal thing I'm aiming for. I think BitTorrent is still the protocol of choice for getting content that hasn't been released locally. Not that I encourage that kind of thing, of course. ;)

---

### Post by nickrout on 2009-04-15
> **Caps18 said:**
> 
There is also the implication that there could be a worldwide Mythbuntu network, and if there was a show in England, Canada, or Australia (or where ever else) that I don't have access to, then this could enable it.  But, I'm sure there could be some copyright issues that would have to be dealt with.

Its called bittorrent or IRC :)

But seriously it is a breach of copyright and I know the myth devs specifically ban such discussion on the main mailing list. I don't imagine they or the mythbuntu devs would welcome such discussion here either.

---

### Post by minirx7 on 2009-04-15
I am getting an error!!!

bash: /usr/local/bin/mythipodcom.sh: /bin/bash^M: bad interpreter: No such file or directory


Not sure why that is happening!  Any ideas?

---

### Post by nickrout on 2009-04-15
> **minirx7 said:**
> I am getting an error!!!

bash: /usr/local/bin/mythipodcom.sh: /bin/bash^M: bad interpreter: No such file or directory


Not sure why that is happening!  Any ideas?

Yes, at a guess you used a windows machine to unpack the files and that dodgy OS added a carriage return (Ctrl-M or ^M) to the end of every line.

Download or transfer the zip file to your linux machine and use unzip to unpack it.

---

### Post by minirx7 on 2009-04-17
> **nickrout said:**
> Yes, at a guess you used a windows machine to unpack the files and that dodgy OS added a carriage return (Ctrl-M or ^M) to the end of every line.

Download or transfer the zip file to your linux machine and use unzip to unpack it.

I didnt use Windows at all.  I used FILEROLLER from my linux box, very strange.

---

### Post by davidstoll on 2009-04-20
I'm getting a mostly blank feed.xml

I tried to edit feed.pl by adding link and custom path information, but it didn't help.  I have mp4 files in the default path.  Any suggestions?


```
<?xml version='1.0' encoding='UTF-8'?>
<rss xmlns:itunes='http://www.itunes.com/dtds/podcast-1.0.dtd' xmlns:atom='http://www.w3.org/2005/Atom' version='2.0'>

<channel>
<title></title>
<description></description>
<link></link>
<itunes:category text='TV &amp; Film'/>
<itunes:subtitle></itunes:subtitle>
<itunes:summary></itunes:summary>
<itunes:author></itunes:author>
<atom:link href='' rel='self' type='application/rss+xml'/>
<itunes:explicit>no</itunes:explicit>

<itunes:owner>
<itunes:name></itunes:name>

<itunes:email></itunes:email>
</itunes:owner>
<itunes:image href=''/>

<copyright></copyright>
<language>en-us</language>

</channel>
</rss>
```

---

### Post by Medieval Cow on 2009-04-23
Thanks for the feedback, all. I think I forgot a step, actually. Unless things have changed since I set up my box, Mythbuntu doesn't come with a version of FFMPEG that would make MP4 files. I believe that can just be fixed by turning on the Medibuntu repository. It's been a while since I set that part up, though. Can anyone confirm if that's the case?

> **minirx7 said:**
> Just a question about RSS Player.  Does it use the native IPOD player?  In other words you hit play, it will see output the video through video output cable right (like youtube)
Yeah, RSS player does use the native player for video. I haven't used an output cable for the video feeds, but I've hooked up headphones/speakers for the audio, so I don't see why outputting video wouldn't work.

> **minirx7 said:**
> I didnt use Windows at all.  I used FILEROLLER from my linux box, very strange.
Were you able to fix that by going in and manually editing the file to take out the ^M? Not sure why that would be happening. I just tried downloading the files myself and they looked ok at a glance.

> **davidstoll said:**
> I'm getting a mostly blank feed.xml

I tried to edit feed.pl by adding link and custom path information, but it didn't help.  I have mp4 files in the default path.  Any suggestions?
That's strange. Did you add the info you added in between the quotes? Can you post the contents of your feed.pl file? As far as it picking up the MP4 files, did you use the included script to convert them? It won't pick them up if the file names are different than the type that generates (that is, just appending a .mp4 for the file name MythTV generates). I could amend the script so it would grab any MP4 file in there, but right now it's set up so it pulls the date, time, and channel out of that file name to give the feed a little more info. Can you post an example of the file names you have in the directory as well, so I can see if that's the problem?

---

### Post by SeanOB on 2009-08-08
FFMPEG doesn't work out of the box - you need to follow the instructions here:
[http://gebaar.blogspot.com/2009/06/howto-easily-enable-mp3-mpeg4-aac-and.html](http://gebaar.blogspot.com/2009/06/howto-easily-enable-mp3-mpeg4-aac-and.html)

For me it was just one apt-get install:
```
sudo apt-get install ffmpeg libavcodec-unstripped-52
```

Next issue was an issue with the transcode scripts - I needed to use this line:
```
ffmpeg -i "${directory}/${file}" -acodec libfaac -ab ${abitrate} -ac 2 -s ${width}x${height} -vcodec mpeg4 -b ${vbitrate} -flags +aic+mv4 -trellis 1 -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 512k -bufsize 2M -metadata title="${file}" "${directory}/${file}.mp4"
```

Which I grabbed from here:
[http://www.mythtv.org/wiki/Streaming_to_iPod_touch_or_iPhone#Transcoding_and_Scripts](http://www.mythtv.org/wiki/Streaming_to_iPod_touch_or_iPhone#Transcoding_and_Scripts)

---

### Post by SeanOB on 2009-08-08
I also sexed up the feed generator using the MythTV module in the perl.
You might have to install some CPAN modules to get it to work - but it's worth it!

Here's what I ended up with:

```

#!/usr/bin/perl -w
# use strict;
use Fcntl; #The Module
use MythTV;
use DateTime;
use DateTime::Format::Mail;

# Generates an iTunes-compatible RSS feed of all MP4 files in the directory

# Fill in the following strings (between the empty quotes) with the information you would like in your RSS Feed
# The title of your feed
$title = "Sean\'s MythTV Box";
# A description of the feed
$description = "Recordings on Sean\'s MythTV Box";
# A link to the folder where your feed and recordings are located. Make sure you do NOT end the link with a "/" (i.e. http://www.example.com/recordings instead of http://www.example.com/recordings/)
$link = "http://example.com/recordings";
$subtitle = "All of the TV on the MythBox";
$summary = "All of the TV on the MythBox";
$author = "Sean";
# A link to the feed itself
$selflink = "http://example.com/recordings/feed.xml";
# Information about the feed's author
$name = "Sean O\'Boyle";
# Your e-mail address. Must include a \ before the @ symbol (e.g., email\@domain.com)
$email = "foo\@example.com";
# A link to an image to use for the feed
$image = "";
#copyright owner for the feed
$copyright = "Copyright Sean";
# Update below if your MythTV recordings are saved to a different location
$file = "/var/myth/recordings/feed.xml";
# Update below to your MythTV recordings directory if different
$directory = "/var/myth/recordings";

# Sets up two arrays to be used later.
@items = ();
@itemnums = ();

# Connect to mythbackend
my $Myth = new MythTV();

# Deletes the current feed if it already exists. Always starts a new feed from scratch to account for deleted recordings
unlink($file);

# Creates a new file and fills in the headers of the feed using the information above
sysopen (XML, $file, O_RDWR|O_EXCL|O_CREAT, 0755);
printf XML "<?xml version='1.0' encoding='UTF-8'?>\n";
printf XML "<rss xmlns:itunes='http://www.itunes.com/dtds/podcast-1.0.dtd' xmlns:atom='http://www.w3.org/2005/Atom' version='2.0'>\n\n";
printf XML "<channel>\n";
printf XML "<title>" . $title . "</title>\n";
printf XML "<description>" . $description . "</description>\n";
printf XML "<link>" . $link . "</link>\n";
printf XML "<itunes:category text='TV &amp; Film'/>\n";
printf XML "<itunes:subtitle>" . $subtitle . "</itunes:subtitle>\n";
printf XML "<itunes:summary>" . $summary . "</itunes:summary>\n";
printf XML "<itunes:author>" . $author . "</itunes:author>\n";
printf XML "<atom:link href='" . $selflink . "' rel='self' type='application/rss+xml'/>\n";
printf XML "<itunes:explicit>no</itunes:explicit>\n\n";
printf XML "<itunes:owner>\n";
printf XML "<itunes:name>" . $name . "</itunes:name>\n";
printf XML "<itunes:email>" . $email . "</itunes:email>\n";
printf XML "</itunes:owner>\n";
printf XML "<itunes:image href='" . $image . "'/>\n\n";
printf XML "<copyright>" . $copyright . "</copyright>\n";
printf XML "<language>en-us</language>\n\n";

# Example format - you can get all of the available options stealing from the mythrename.pl script
$format = '%T %- %Y-%m-%d, %g-%i %A %- %S';

# Iterates through the directory picking out all the .MP4 files
foreach $f (<$directory/*>) {
	if ( $f =~ /\.mp4$/ ){
		$f =~ s/\.mp4$//;
		# Stores just the name of the file for use in generating the feed later
		if ($f =~ /([0-9].*)/){
			$filename = $1;
		}
		# Connect to the database
		$show = $Myth->new_recording($f);
		#print "Info: ".$show."\n";
		$name = $show->format_name($format, '-', '_', 1, 0, 1);
		#print "Name: ".$name."\n";

		$title = $show->format_name('%T', ' ', ' ', 1, 0, 1);
		#print "Title: ".$title."\n";
		$episode = $show->format_name('%S', ' ', ' ', 1, 0, 1);
		#print "Episode: ".$episode."\n";
		$summary = $show->format_name('%R', ' ', ' ', 1, 0, 1);
		#print "Summary: ".$summary."\n";

		$channel = $show->format_name('%cn', ' ', ' ', 1, 0, 1);
		#print "Channel: ".$channel."\n";
		$callsign = $show->format_name('%cc', ' ', ' ', 1, 0, 1);
		#print "Channel: ".$callsign."\n";

		$year = $show->format_name('%Y', ' ', ' ', 1, 0, 1);
		#print "Year: ".$year."\n";
		$month = $show->format_name('%m', ' ', ' ', 1, 0, 1);
		#print "Month: ".$month."\n";
		$day = $show->format_name('%d', ' ', ' ', 1, 0, 1);
		#print "Day: ".$day."\n";
		$starthour = $show->format_name('%G', ' ', ' ', 1, 0, 1);
		#print "StartHour: ".$starthour."\n";
		$startmin = $show->format_name('%i', ' ', ' ', 1, 0, 1);
		#print "StartMin: ".$startmin."\n";
		$startsec = $show->format_name('%s', ' ', ' ', 1, 0, 1);
		#print "StartSec: ".$startsec."\n";
		$origair = $show->format_name('%om/%od/%oY', ' ', ' ', 1, 0, 1);
		#print "Orig: ".$origair."\n";

		my $dt = DateTime->new(
			year => $year, month => $month, day => $day,
			hour => $starthour, minute => $startmin, second => $startsec,
			time_zone => "local"
		);

		$str2822date = DateTime::Format::Mail->format_datetime( $dt );
		#print $str2822date."\n";

		$length = -s $f . ".mp4";

		# Break File Path / Name into ItemNum Identifier Number
		$f =~ s/\.mpg$//;
		$f =~ s/$directory\///;
		$f =~ s/\_//;
		$itemnum = $f;

		# Adds the item information for each .MP4 file to the a string using the information pulled from the file name above
		$item = "<item>\n";
		$item = $item . "<title>" . $title . " - " . $episode ." </title>\n";
		$item = $item . "<itunes:author>" . $title . "</itunes:author>\n";
		$item = $item . "<pubDate>" .$str2822date ."</pubDate>\n";
		$item = $item . "<itunes:summary>Channel: " . $channel . " - " . $callsign . "\n\n" . $title . " - " . $episode ."\n\n". $summary ."\n\n" ."Original Airdate: " . $origair . "\n" . "</itunes:summary>\n";
		$item = $item . "<itunes:subtitle>" . $summary . "</itunes:subtitle>\n";
		$item = $item . "<link>" . $link . "</link>\n";
		$item = $item . "<enclosure url='" . $link . "/" . $filename . ".mp4' length='" . $length . "' type='video/mp4'></enclosure>\n";
		$item = $item . "<guid>" . $link . "/" . $filename . ".mp4</guid>\n";
		$item = $item . "<itunes:explicit>no</itunes:explicit>\n";
		$item = $item . "<itunes:keywords>MythTV Feed</itunes:keywords>\n";
		$item = $item . "</item> \n\n";

		# Adds the $item string created above into an array ordered by the recording date, newest items first. This allows the feed to be generated with the newest items at the top
		$x = 0;
		$replaced = "no";
		$total = @itemnums;

		# If this is the first time through, simply adds the item to the array
		if ($total eq 0){
				@itemnums = ($itemnum);
				@items = ($item);
				$replaced = "yes";
			}
		# Inputs all subsequent items into the array based on their record date as described above. $itemnum is the year, month, day, and time of the recording in one string, in that order, so it can be used to sort them.
		# Runs through an array of  the $itemnum strings of each corresponding $item. When it finds the proper place in the @itemnum array, adds the $item into the same spot in the @items array
		else{
			while ($x < $total && $replaced eq 'no'){
				if ($itemnum > $itemnums[$x]){
					splice (@itemnums, $x, 0, $itemnum);
					splice (@items, $x, 0, $item);
					$replaced = "yes";
				}
				else{
					$x++;
				}
			}
		}
		# If the $item has been compared to all of the items in the array and is found to be older than all of them, it is added to the end of the array
		if ($replaced eq "no"){
			@itemnums = (@itemnums, $itemnum);
			@items = (@items,$item);
		}
	}
}
# Prints the array @items to the feed
printf XML "@items";
# Adds the closing tags for the feed and closes out the file
printf XML "</channel>\n";
printf XML "</rss>";
close(XML);





```

---

### Post by ktmom on 2009-09-15
I can't make this work as either a user job or as a stand-alone script.  Myth fails the job complaining it can not find the executable:

```
2009-09-15 14:41:13.973 JobQueue: Started "Myth iPod" for "True Jackson, VP" recorded from channel 1025 at Sun Sep 13 19:30:00 2009
sh: /usr/local/bin/mythipodcom.sh: not found
2009-09-15 14:41:13.997 JobQueue Error: User Job '/usr/local/bin/mythipodcom.sh' failed, unable to find executable, check your PATH and backend logs.
2009-09-15 14:41:13.999 JobQueue: Current PATH: '/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin'

```

if I run it from the terminal I get:
```
ktmom@mythbox:/var/lib/mythtv/recordings$ sh /usr/local/bin/mythipodcom.sh 1025_20090914183000.mpg
: not foundbin/mythipodcom.sh: 2: 
: not foundbin/mythipodcom.sh: 7: 
: not foundbin/mythipodcom.sh: 11: 
/usr/local/bin/mythipodcom.sh: 104: Syntax error: end of file unexpected (expecting "then")

```

the permissions are all there.  It goes ahead and runs the feed.pl ok both within myth and from the command line.  Any ideas what I might be doing wrong?

---

### Post by rumy on 2010-09-24
Hey,

I am getting a 403 permission error.

Any suggestions on how to fix that.

I am new to linux so please help. thanks

---

### Post by winewood on 2010-12-26
hey! I just got this working.  Thank you very much for all the time you spend in hooking us up with that feed script.  It is perfect for downloading the video to our ipods, that is transcoded.

I made my work with mythipodcom.sh which honors the commercials.  I modified mine after looking from another example.


Below is a modified mythipodcom.sh (honors cutlists) that I am using.

```
#!/bin/bash

#MythIPod v.1 http://www.chiefhacker.com/
#Copyright 2007 Chris Lorenzo et al
#This software is licensed under the CC-GNU LGPL <http://creativecommons.org/licenses/LGPL/2.1/>
#Additionally modified 2007 Doug Johnson

#!/bin/sh
VIDEODIR=$1
FILENAME=$2

if [ -f "$VIDEODIR/$FILENAME.mp4" ]; then
        rm -f $VIDEODIR/$FILENAME.mp4
fi

# Sanity checking, to make sure everything is in order.
if [ -z "$VIDEODIR" -o -z "$FILENAME" ]; then
        echo "Usage: $0 <VideoDirectory> <FileName>"
        exit 5
fi
if [ ! -f "$VIDEODIR/$FILENAME" ]; then
        echo "File does not exist: $VIDEODIR/$FILENAME"
        exit 6
fi
# The meat of the script. Flag commercials, copy the flagged commercials to
# the cutlist, and transcode the video to remove the commercials from the
# file.
#mythcommflag -f $VIDEODIR/$FILENAME
#ERROR=$?
#if [ $ERROR -gt 126 ]; then
#        echo "Commercial flagging failed for ${FILENAME} with error $ERROR"
#        exit $ERROR
#fi
mythcommflag --gencutlist -f $VIDEODIR/$FILENAME
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Copying cutlist failed for ${FILENAME} with error $ERROR"
        exit $ERROR
else
        echo "Copying cutlist successful for ${FILENAME}."
fi

CUTLIST=$(mythcommflag --getcutlist -f $VIDEODIR/$FILENAME | tail -n 1 | awk '{print $2}' | sed 's/,/ /g')
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Copying cutlist failed for ${FILENAME} with error $ERROR"
        exit $ERROR
fi

mythtranscode --mpeg2 -i $VIDEODIR/$FILENAME --honorcutlist "$CUTLIST" -o $VIDEODIR/$FILENAME.tmp

ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Transcoding failed for ${FILENAME} with error $ERROR"
        exit $ERROR
fi

mythcommflag --clearcutlist -f $VIDEODIR/$FILENAME
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Clearing cutlist failed for ${FILENAME} with error $ERROR"
        rm /usr/video/$FILENAME.tmp
        exit $ERROR
fi

#Begin mythipod script
if [ ! $# == 2 ]; then
  echo "Usage: $0 directory file"
  exit
fi

directory="$1";
file="$2";

#Get the video information
video_info=`mplayer -vo null -ao null -frames 10 -identify "${directory}/${file}" 2>/dev/null`

#Command line grep sucks, but we make due...
aspect=`echo $video_info | egrep -oe "Movie-Aspect is [0-9:.]+" | egrep -o "[0-9:.]+"`
framerate=`echo $video_info | egrep -oe "[0-9.]+ fps" | egrep -o "[0-9.]+"`

# set resolution by aspect ratio

if [ "$aspect" == "1.78:1" ]
then
  width=432
  height=240
  vbitrate=480k
else
  width=480
  height=360
  vbitrate=378k
fi

abitrate=128k
# Figure out which AAC we have
AAC=$(ffmpeg -v 2>&1|sed "s/--enable-/\n/g"|grep aac|awk '{print $1}')
if [ "x${AAC}" = "libfaac" ]
then
        ACODEC="-acodec libfaac"
else
        ACODEC="-acodec aac"
fi

# Create the MP4

ffmpeg -i "${directory}/${file}.tmp" $ACODEC -ab ${abitrate} -ac 2 -s ${width}x${height} -vcodec mpeg4 -b ${vbitrate} -flags +aic+mv4 -trellis 1 -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 512k -bufsize 2M -metadata title="${file}" "${directory}/${file}.mp4"

#ffmpeg -i "${directory}/${file}.tmp" -acodec aac -ab ${abitrate} -ac 2 -s ${width}x${height} -vcodec mpeg4 -b ${vbitrate} -flags +aic+mv4+trell -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 512k -bufsize 2M -title "${file}" "${directory}/${file}.mp4"

# remove the temporary file

rm -f "${directory}/${file}.tmp"

```




#This checks to see if transcodeing is happening to see if it is safe to run.

I found that many of my mp4's were made in another directory called livetv.  I created a script that looked to see if mythtranscode was running, and if so, moved them to the recorded directory.

```
#!/bin/bash

if [ ! "$(pgrep mythtranscode)" ]
then
        #This will move all files associated with mp4 and move them to the /opt/recordings directory
        # Yes, you will have to edit the cut -c numbers to print out the name of your video files if your directory name is different.
        for x in `ls /opt/livetv/*.mp4 | cut -c 13-31`
                do
                name="$x""*"
                mv /opt/livetv/$name /opt/recordings
        done
fi

```

Hope this helps, and thanks a ton!

---

