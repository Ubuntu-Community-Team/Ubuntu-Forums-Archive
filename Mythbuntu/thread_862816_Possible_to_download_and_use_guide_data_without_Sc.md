---
title: "Possible to download and use guide data without Schedule's Direct in USA?"
date: 2008-07-17
forum: Mythbuntu
---

### Post by SSVegito888 on 2008-07-17
Is it possible to download and use guide data without using Schedule's Direct in USA with regular cable (NOT DIGITAL)?  If so, how?



Thanks,

SSVegito888

---

### Post by tgm4883 on 2008-07-17
Depending on your location you might be able to use EPG.  You could also screen scrape although IMHO thats pretty much worthless.

---

### Post by theophile on 2008-07-18
I've been using [this]("http://zap2xml.110mb.com/") since the free listings were discontinued a year ago. It is great and supports genres, rerun flag, HD flag, etc, etc.

Here's the script I run as a cron job. This has been giving me listings flawlessly for at least a year.

Create /usr/share/mythtv/zap2xml
Create /usr/share/mythtv/zap2xml/cache
Create /usr/share/mythtv/zap2xml/logs
Download zap2xml.pl and put it in /usr/share/mythtv/zap2xml
Follow the instructions at the zap2xml website for setting up your zap2it account
Put this script at /usr/local/bin/mythupdate.sh and make it executable:
```
#!/bin/bash

WorkDir="/usr/share/mythtv/zap2xml"
user1="your@email.address"
password1="yourpassword"
user2=""
password2=""


cd $WorkDir


#check for logs dir, create it if it doesnt exist
if [ ! -d logs ]; then
  mkdir logs
fi


#delete the previous days older then 4 days
#create the rest of the date stamps
for ((i=5;i<=20;i+=1)); do
   rmday=`date +%Y --date="-$i days"``date +%m --date="-$i days"``date +%d --date="-$i days"`
   rm $WorkDir/logs/zap2xml.$rmday.* >/dev/null 2>&1
done


#create timestamps
day0=`date +%Y``date +%m``date +%d`
echo "----------------------------------" > $WorkDir/logs/zap2xml.$day0.log
echo "zap2xml.$day0.log" >> $WorkDir/logs/zap2xml.$day0.log


#Run full update if Monday and three days rest of week.
if [ "`date +%u`" == "1" ] ; then
   pd=15
else
   pd=3
fi


echo "Running zap2xml.pl..." >> $WorkDir/logs/zap2xml.$day0.log
echo "----------------------------------" >> $WorkDir/logs/zap2xml.$day0.log
#$WorkDir/zap2xml.pl -u $user2 -p $password2 -o $WorkDir/logs/zap2xml.$day0.alt.xml -c $WorkDir/cache_alt -d $pd -N $pd -L -x >> $Wo                         rkDir/logs/zap2xml.$day0.log 2>> $WorkDir/logs/zap2xml.$day0.log
$WorkDir/zap2xml.pl -u $user1 -p $password1 -o $WorkDir/logs/zap2xml.$day0.xml -c $WorkDir/cache -d $pd -N $pd -A -L >> $WorkDir/log                         s/zap2xml.$day0.log 2>> $WorkDir/logs/zap2xml.$day0.log


# Next 4 Lines - Remove "To Be Announced" and "Paid Programming"
#cat $WorkDir/logs/zap2xml.$day0.alt.xml | grep "m='SH000000010000" -v | grep "m='SH000191680000" -v > $WorkDir/logs/zap2xml.x.alt.x                         ml
#mv $WorkDir/logs/zap2xml.x.alt.xml $WorkDir/logs/zap2xml.$day0.alt.xml
cat $WorkDir/logs/zap2xml.$day0.xml | grep "m='SH000000010000" -v | grep "m='SH000191680000" -v > $WorkDir/logs/zap2xml.x.xml
mv $WorkDir/logs/zap2xml.x.xml $WorkDir/logs/zap2xml.$day0.xml

### get lineupid by doing: grep "lineup" xtvd.xml
### &lt;lineups&gt;
###        &lt;lineup id="FL09523:-" name="Comcast Broward CO" location="33441" type="Cable" postalcode="33441"&gt;
###        &lt;/lineup&gt;
### &lt;/lineups&gt;


echo "----------------------------------" >> $WorkDir/logs/zap2xml.$day0.log
echo "Running mythfilldatabase..." >> $WorkDir/logs/zap2xml.$day0.log
echo "----------------------------------" >> $WorkDir/logs/zap2xml.$day0.log
#mythfilldatabase --refresh-all --dd-file 5 -1 FL09523:X $WorkDir/logs/zap2xml.$day0.alt.xml >> $WorkDir/logs/zap2xml.$day0.log 2>>                          $WorkDir/logs/zap2xml.$day0.log
MYTHCONFDIR=/home/.mythtv mythfilldatabase --refresh-all --file 1 $WorkDir/logs/zap2xml.$day0.xml >> $WorkDir/logs/zap2xml.$day0.log                          2>> $WorkDir/logs/zap2xml.$day0.log


echo "----------------------------------" >> $WorkDir/logs/zap2xml.$day0.log
echo "Errors???..." >> $WorkDir/logs/zap2xml.$day0.log
echo "----------------------------------" >> $WorkDir/logs/zap2xml.$day0.log
#Check For Invalid Dates
#cat $WorkDir/logs/zap2xml.$day0.alt.xml | grep "duration='PT" | grep "duration='PT0" -vc >> $WorkDir/logs/zap2xml.$day0.log
cat $WorkDir/logs/zap2xml.$day0.xml     | grep "duration='PT" | grep "duration='PT0" -vc >> $WorkDir/logs/zap2xml.$day0.log


#echo "Running email report..."
#cat $WorkDir/email_base $WorkDir/logs/zap2xml.$day0.log | /usr/sbin/sendmail -t
```
Then run it and cross your fingers. ;-)

The way I do it, is I delete all my channels and make sure I add all the channels I want to my zap2it lineup. Then running mythupdate.sh will create all the channels in MythTV and download all the guide data for them. Then you can go into the channel editor and assign them to the relevant sources.

The script grabs two weeks' worth of data on Mondays, and every other day, it just looks three days out and makes updates if necessary. This is for speed and to prevent unnecessarily hitting the zap2it servers every day.

The script also caches the data for these reasons. If something goes amiss, you can review the logs in /usr/share/mythtv/zap2xml/logs

---

### Post by SSVegito888 on 2008-07-18
Thanks for the tip;I will try this.


Also, I am new to Linux, so thanks for the step by step instructions!!!



Thanks,

SSVegito888

---

### Post by SSVegito888 on 2008-07-18
I just have 3 more questions.


1. How often do I set the cron job to run?


2. Is .pl a perl script?


3. I am running Ubuntu 8.04 Hardy, are there any unresolved dependecies that I need to worry about?


Thanks,

SSVegito888

---

### Post by theophile on 2008-07-19
I run the cron job once a day, at 4 am. You could probably get away with running it only on Mondays and once more during the week.

Yes, .pl is a perl script.

And no, all dependencies are met on stock Mythbuntu install. In fact, since the Mythbuntu installer nuked my backup partition, I just had to do a fresh install and this script worked great. In fact, I have it pulling data for two video sources and I will probably tweak it to add a third.

---

### Post by theophile on 2008-08-11
Here's a quick update to this thread, as there's a new utility called [mc2xml](http://mc2xml.110mb.com/) which generates EPG data from Windows Media Center servers rather than Zap2it. This results in much more robust listings which include better credits, more detailed plot info and episode guides, and movie ratings. I've just gotten it working with multiple sources and here's how I did it. If you're only using one source, the changes are trivial:

[LIST=1]
[*]Create /usr/share/mythtv/mc2xml
[*]Download the script from [here](http://mc2xml.110mb.com/f.php?f=mc2xml) and place it at /usr/share/mythtv/mc2xml/mc2xml
[*]```
chmod 755 /usr/share/mythtv/mc2xml/mc2xml
```
[*]Create data directories for each source. In my case, I have one source for firewire and one for s-video, so I made /usr/share/mythtv/mc2xml/firewire/ and /usr/share/mythtv/mc2xml/svideo/ .
[/LIST]

Next, we need to tell the script which channels we want in the lineup for each source:
[LIST=1]
[*]```
nano -w /usr/share/mythtv/mc2xml/firewire/mc2xml.chl
```
[*]Type in the number of every channel you want for this source, one number per line. In my case, I use firewire for HD, so I just put each HD channel number on its own line.
[*]Repeat for each unique source, putting a mc2xml.chl file in each data directory created above, corresponding to the channels to grab for that source.
[/LIST]

Now select the lineup for each source. For non-US users, change "us" in step 2 to your country code.:
[LIST=1]
[*]```
cd /usr/share/mythtv/mc2xml
```
[*]```
./mc2xml -c us -g [ZIPCODE] -o firewire/data.xml -D firewire/mc2xml.dat -C firewire/mc2xml.chl
```
[*]A dialog will appear, giving you a choice of data sources for your location. Choose the appropriate one.
[*]Now wait a moment as the initial data is gathered and written to the appropriate files.
[*]Repeat for each unique source, changing the paths as appropriate.
[/LIST]

Upon setting up mc2xml for the first time, you have to run mythfilldatabase manually for each source. This is because, unlike zap2xml, the new mc2xml uses a unique "version" string in the mc2xml.dat file. This means that when mc2xml is run, it will not write a new xml file if the listings source has not been changed since the last time it was run. Since the script below includes the data fetching, it will not work if the source data file has recently been updated (as it just was, since we just created it!)

So we update MythTV manually for the first run. Replace the number after "--file" with the correct "sourceid" for your particular source:
[LIST=1]
[*]```
cd /usr/share/mythtv/mc2xml
```
[*]```
mythfilldatabase --refresh-all --file 1 firewire/data.xml
```
[*]Repeat for other sources, changing the paths and sourceid as necessary.
[/LIST]

At this point, if you already had channel and program data, you are likely to have duplicate channels. You can either delete all your old channels and use the new ones created by this script, or you can do what I did, since I had custom named each channel and hand-picked my channel icons.

Clean up channels in the database:
[LIST=1]
[*]Log in to MythWeb
[*]Go to Settings --> TV --> Channel Info
[*]Here you have a list of your channels. If you look, you will probably see the duplicate channels listed one after the other, each having the same "channum" value but having different "xmltvid" values. The "xmltvid" value is how MythTV identifies unique channels. Since mc2xml gets its data from Microsoft servers, you want to make sure that the xmltvid string that ends in microsoft.com is the string you use.
[*]Copy and paste the "xmltvid" field from the newly added channel to the same field in the previously existing channel with the same "channum" value.
[*]Repeat this process for all duplicate channels, then delete the "new" duplicate channels.
[*]All unique channels should now have an xmltvid that ends in microsoft.com 
[/LIST]

Okay, now we set it up to automatically update. This is the script from earlier in the thread, updated to use mc2xml. If you've been modifying the instructions to this point, you'll have to make the same changes to the script:

```
#!/bin/bash

WorkDir="/usr/share/mythtv/mc2xml"

cd $WorkDir


#check for logs dir, create it if it doesnt exist
if [ ! -d logs ]; then
  mkdir logs
fi


#delete the previous days older then 4 days
#create the rest of the date stamps
for ((i=5;i<=20;i+=1)); do
   rmday=`date +%Y --date="-$i days"``date +%m --date="-$i days"``date +%d --date="-$i days"`
   rm $WorkDir/logs/mc2xml.$rmday.* >/dev/null 2>&1
done


#create timestamps
day0=`date +%Y``date +%m``date +%d`
echo "----------------------------------" > $WorkDir/logs/mc2xml.$day0.log
echo "mc2xml.$day0.log" >> $WorkDir/logs/mc2xml.$day0.log

echo "Running mc2xml.pl..." >> $WorkDir/logs/mc2xml.$day0.log
echo "----------------------------------" >> $WorkDir/logs/mc2xml.$day0.log
$WorkDir/mc2xml -D $WorkDir/firewire/mc2xml.dat -C $WorkDir/firewire/mc2xml.chl -o $WorkDir/logs/mc2xml.$day0.fw.xml -L >> $WorkDir/logs/mc2xml.$day0.log 2>> $WorkDir/logs/mc2xml.$day0.log
$WorkDir/mc2xml -D $WorkDir/svideo/mc2xml.dat -C $WorkDir/svideo/mc2xml.chl -o $WorkDir/logs/mc2xml.$day0.svideo.xml -L >> $WorkDir/logs/mc2xml.$day0.log 2>> $WorkDir/logs/mc2xml.$day0.log


# Next 5 Lines - Remove "HDTV" flag from standard definition sources
if [ -f $WorkDir/logs/mc2xml.$day0.svideo.xml ]; then
  cat $WorkDir/logs/mc2xml.$day0.svideo.xml | grep "<quality>HDTV</quality>" -v > $WorkDir/logs/mc2xml.x.svideo.xml
  mv $WorkDir/logs/mc2xml.x.svideo.xml $WorkDir/logs/mc2xml.$day0.svideo.xml
fi

echo "----------------------------------" >> $WorkDir/logs/mc2xml.$day0.log
echo "Running mythfilldatabase..." >> $WorkDir/logs/mc2xml.$day0.log
echo "----------------------------------" >> $WorkDir/logs/mc2xml.$day0.log
#mythfilldatabase --refresh-all --dd-file 5 -1 FL09523:X $WorkDir/logs/zap2xml.$day0.alt.xml >> $WorkDir/logs/zap2xml.$day0.log 2>>                          $WorkDir/logs/zap2xml.$day0.log
MYTHCONFDIR=/home/.mythtv mythfilldatabase --refresh-all --file 1 $WorkDir/logs/mc2xml.$day0.fw.xml >> $WorkDir/logs/mc2xml.$day0.log 2>> $WorkDir/logs/mc2xml.$day0.log
MYTHCONFDIR=/home/.mythtv mythfilldatabase --refresh-all --file 2 $WorkDir/logs/mc2xml.$day0.svideo.xml >> $WorkDir/logs/mc2xml.$day0.log 2>> $WorkDir/logs/mc2xml.$day0.log

echo "----------------------------------" >> $WorkDir/logs/mc2xml.$day0.log
echo "Errors???..." >> $WorkDir/logs/mc2xml.$day0.log
echo "----------------------------------" >> $WorkDir/logs/mc2xml.$day0.log
#Check For Invalid Dates

if [ -f $WorkDir/logs/mc2xml.$day0.svideo.xml ]; then
  cat $WorkDir/logs/mc2xml.$day0.svideo.xml | grep "duration='PT" | grep "duration='PT0" -vc >> $WorkDir/logs/mc2xml.$day0.log
fi

if [ -f $WorkDir/logs/mc2xml.$day0.fw.xml ]; then
  cat $WorkDir/logs/mc2xml.$day0.fw.xml | grep "duration='PT" | grep "duration='PT0" -vc >> $WorkDir/logs/mc2xml.$day0.log
fi
```

I commented out some sections that I haven't been able to test yet, but this should work. Put it at /usr/local/bin/mythupdate2.sh and "chmod 755" it.

Remember, if you run it immediately, it probably won't work since the sources haven't had time to update yet. Wait a few hours (or a whole day to be safe) before running it for the first time. Check the /usr/share/mythtv/mc2xml/logs/ directory for the timestamped logfile if something goes wrong.

Lastly, set up a cron job to run it every day:
[LIST=1]
[*]```
nano -w /etc/crontab
```
[*]I use the following line: ```
0  4    * * *   root    /usr/local/bin/mythupdate2.sh
```
[/LIST]

Remember, if you have been using the zap2xml script as a cron job, remove that line or else zap2xml will re-create the old channels and you'll have duplicates again.

Hope this helps!

---

### Post by nickrout on 2008-08-11
What is the licensing of the mc2xml program? And where can I get the source (assuming it is free software)

---

### Post by theophile on 2008-08-11
Can't answer either of those questions, but there's a contact email address at the bottom of the website.

---

### Post by nickrout on 2008-08-11
sorry i thought from your useful and detailed guide you may have been the author!

---

### Post by theophile on 2008-08-11
Oh, no. Sadly, I am just the messenger. :)

---

### Post by InTheZone on 2008-08-18
What version of Mythbuntu are you running mc2xml on? I downloaded the new version released on 08/14/2008 and it doesn't seem to work. I run it and it exits immediately. I get no message stating what version it is or anything. Is anyone else having this problem? I am running mythbuntu 8.04.1. It is a new load and right now I am using zap2xml to fill the programming data.

---

### Post by theophile on 2008-09-11
InTheZone, could you be more specific? What is the output of the mc2xml process?

Also, I have updated the mythupdate.sh script in post #7 in page 1. The new version of the script now strips the HDTV tag out of non-HD channel sources so analog channels do not report HD programming. Also, since mc2xml does not pull new data if the data source has not been updated, the script now checks to see if new data has been pulled before proceeding.

I have had this system set up and running flawlessly without any intervention since the original date of post #7. Hope others are able to make use of it!

---

### Post by InTheZone on 2008-10-03
Hi theophile,
I have located the problem. I am running the 64-bit version of mythbuntu and according to the mc2xml website you must install the libc6-i386 package. It is working correctly now.

Thanks

---

### Post by SSVegito888 on 2008-10-24
I am having a couple of problems.

> Create /usr/share/mythtv/mc2xml

already did this. So I am done with this step.


> Download the script from here and place it at /usr/share/mythtv/mc2xml/mc2xml



are you talking about the update.sh script?


where exactly do I place the mc2xml linux executable file?


> Create data directories for each source. In my case, I have one source for firewire and one for s-video, so I made /usr/share/mythtv/mc2xml/firewire/ and /usr/share/mythtv/mc2xml/svideo/


I am using a hauppauge WinTV-PVR 150.

So, do I use the name Tuner 1 or the optional name I gave it "WinTV-PVR"?

---

### Post by t3chn0b0y on 2008-10-26
Thanks this is very informative , I really like how you explained things step by step.. Now Im back in business... ;):popcorn:

---

### Post by theophile on 2008-11-14
Sorry about forgetting about this post. Son was born 3 weeks ago, quite hectic around here!

> **SSVegito888 said:**
> are you talking about the update.sh script?


where exactly do I place the mc2xml linux executable file?

This set is talking about the mc2xml binary file, as obtained from the mc2xml website. One way to do this is:
```
wget http://mc2xml.110mb.com/?t=mc2xml -O /usr/share/mythtv/mc2xml/mc2xml
```

> **SSVegito888 said:**
> I am using a hauppauge WinTV-PVR 150.

So, do I use the name Tuner 1 or the optional name I gave it "WinTV-PVR"?
You can name the directories anything you want, *as long as you are consistent!*

The way I wrote the howto, you are using one binary for mc2xml to maintain two separate data directories for two separate data sources. If you're only using one tuner, you only need one data source. In that case, you don;t even necessarily have to create another subdirectory. You could allow the mc2xml binary and all the data live in /usr/share/mythtv/mc2xml/ if you want. 

The important thing is to make sure the /usr/local/bin/mythupdate2.sh script is modified to reflect the proper locations. If you look at that script, you will see that many lines are duplicated with the only changes being in the paths. This is because each command is being repeated twice, once for each data source. I am actually using three data sources now (S-video, Firewire, and OTA ATSC) so my personal script has each line three times.

Good luck with everything. Let me know if you need more help.

---

### Post by tgm4883 on 2008-11-14
As far as I can tell, both of the methods described in this thread violate each of those sites ToS.  Neither of these methods are official supported, and either of them may be illegal.  If this is not the case please PM me and we can discuss it, otherwise do not open another thread regarding these two methods.

---

