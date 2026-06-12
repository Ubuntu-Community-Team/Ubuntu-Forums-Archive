---
title: "xmltv + Firefox = TvFox"
date: 2008-07-12
forum: Multimedia Software
---

### Post by Monstermagnet on 2008-07-12
Hello all,

if you are looking for a full featured tv guide, for display your xmltv or compatible parser output, in your favorite browser,  TvFox is for you.

With TvFox you can mark your favorite shows and categories, set reminders, switch channels and do recordings.

This is the first public announcement, so please let me know what you think.

Please visit [http://tvfox.bplaced.net](http://tvfox.bplaced.net), to get more info or play with the LIVE DEMO.

TvFox is licensed under the GPL v.3, so you are welcome to contribute.

Translators are also welcome, to fix my broken English or to translate to your language.

Thanks and i hope you enjoy TvFox as much as i do.:guitar:

---

### Post by lovinglinux on 2008-09-10
I was looking for something like this for a looooong time. I have tested almost every EPG available, from Windows Media Center to XSLTv. I currently use Freeguide because XSLTv is kind of limited for my needs. But I really wanted something that I could open inside Firefox. Thank you very much.

If you need a translator for Brazilian Portuguese, please let me know.

I'm writing a tutorial on how to use Firefox as a fake "Media Center" and I have included TvFox. Please let me know if you require more credits and links. You can take a look at [http://ubuntuforums.org/showthread.php?p=5748047](http://ubuntuforums.org/showthread.php?p=5748047)

---

### Post by Jose Catre-Vandis on 2008-10-17
> **Monstermagnet said:**
> Hello all,

if you are looking for a full featured tv guide, for display your xmltv or compatible parser output, in your favorite browser,  TvFox is for you.

Just paste your xml file into the TvFox directory and start TvFox.html with Firefox.

With TvFox you can mark your favorite shows and categories, set reminders, switch channels and do recordings.

This is the first public announcement, so please let me know what you think.

Please visit [http://tvfox.bplaced.net](http://tvfox.bplaced.net), to get more info or play with the LIVE DEMO.

TvFox is licensed under the GPL v.3, so you are welcome to contribute.

Translators are also welcome, to fix my broken English or to translate to your language.

Thanks and i hope you enjoy TvFox as much as i do.:guitar:


Many thanks for this, works well.

Is it possible to have channels sorted as per the xmltv file, as opposed to simply alphabetically. For example would like list to go BBC1, BBC2, BBC3, BBC4 but currently displays BBC Four, BBC One, BBC Three, BBC Two?

Is there a setting in the xsl template that would sort this out?

Also, if I set reminders, they only seem to last for that immediate session. If i shut Firefox and then re-open TvFox, the reminders are gone. Similarly if I go to the reminders tab and refresh the page they also disappear.

Thanks

---

### Post by Monstermagnet on 2008-10-18
Hello,

nice that it works well for you.

If you want to have the channels listed as they are sorted in your xmltv file, you can edit the TvFox.xsl file in the xsl directory at line 61

change

```
  <xsl:template name="page1">
    <table id="pageOneContent">
      <xsl:for-each select="tv/channel">
        <xsl:sort select="display-name"/>
        <xsl:call-template name="subpage1">
```

to

```
  <xsl:template name="page1">
    <table id="pageOneContent">
      <xsl:for-each select="tv/channel">
        <!--xsl:sort select="display-name"/-->
        <xsl:call-template name="subpage1">
```

The reminders are not stored, because i use "Global reminders" (requires TvFoxEx Extension), that has the advantage that you will be notified even if TvFox is not running.

I will try to implement that reminders will be stored and make channel sorting an option in the settings tab. This will take some time so don't expect an update too soon.

Thanks for your feedback.

---

### Post by Jose Catre-Vandis on 2008-10-19
> **Monstermagnet said:**
> Hello,

nice that it works well for you.

If you want to have the channels listed as they are sorted in your xmltv file, you can edit the TvFox.xsl file in the xsl directory at line 61

change

```
  <xsl:template name="page1">
    <table id="pageOneContent">
      <xsl:for-each select="tv/channel">
        <xsl:sort select="display-name"/>
        <xsl:call-template name="subpage1">
```

to

```
  <xsl:template name="page1">
    <table id="pageOneContent">
      <xsl:for-each select="tv/channel">
        <!--xsl:sort select="display-name"/-->
        <xsl:call-template name="subpage1">
```

The reminders are not stored, because i use "Global reminders" (requires TvFoxEx Extension), that has the advantage that you will be notified even if TvFox is not running.

I will try to implement that reminders will be stored and make channel sorting an option in the settings tab. This will take some time so don't expect an update too soon.

Thanks for your feedback.

Yeay brilliant! Took me a while to spot the difference in the code :)

---

### Post by Monstermagnet on 2008-10-20
Glad you got it working as expected :) ,

and BTW i have made good progress with the reminder storage, i will release a beta version in a few days.

---

### Post by Monstermagnet on 2008-10-22
Hello,

here's the promised beta version, please test and report bugs.

The beta is only available here.

Thanks

---

### Post by Jose Catre-Vandis on 2008-10-22
Thanks, will give it a go

---

### Post by Jose Catre-Vandis on 2008-10-23
Verion 0.2 works well, I like the reminder with sound! A few requests?

1. can the reminder dialog (which comes up at the set time), a) come up a minute or so before the programme starts, and b) have the dialog appear above all other windows/tabs in case you have sound off or are away from the PC?

2. is it possible to look ahead more than 6/7 hours, say at 10 pm tonight I want to set reminders for tomorrow nights viewing, or even for further ahead than that say in three or four days time?

3. Would like to try out the watch tv and record tv features. I currently use mplayer for both of these running a couple of bash scripts with zenity. To watch tv the eventual command is: ```
 mplayer dvb://BBC1
``` with the channel name coming from ~/.mplayer/channels.conf.
To record tv I use the following eventual command:```
mplayer dvb://BBC1 -dumpstream -dumpfile BBC1Recording.ts
``` - filesize/type not being a problem for me so no need to transcode.
I couldn't see a script for watching tv in the examples, nor is there a menu listing to do this on right click, and how would i write the python scripts to do this with the TvFox extension?

Many thanks again, a great extension to my PC use :)

---

### Post by Monstermagnet on 2008-10-24
> 1. can the reminder dialog (which comes up at the set time), a) come up a minute or so before the programme starts.

Yes, could be done, but if you try the TvFoxExtension you will not use the reminder tab to often. But i will think about it...

> and b) have the dialog appear above all other windows/tabs in case you have sound off or are away from the PC?

It's only possible to open a new window or tab that shows the dialog, so it's better to do this with the TvFoxExtension and a program like kalarm.

> is it possible to look ahead more than 6/7 hours, say at 10 pm tonight I want to set reminders for tomorrow

Click on the arrows beside the timebar...

> or even for further ahead than that say in three or four days time

Processing large xml files becomes very slow, so it's recommend to only load daily files into TvFox.
That's why i haven't implemented that feature and because i'm not interessted what's on tv tomorrow...

Never say never, so maybe i will implement that feature...

> I couldn't see a script for watching tv in the examples, nor is there a menu listing to do this on right click, and how would i write the python scripts to do this with the TvFox extension?

You don't need to do it in python, use what ever you like.

To change a channel you simply click on the networkname or if you use images/logos on that.
(Not only in the tvguide also on the reminder dialog)
In the TvFoxEx Preferences add the path to your script under channelswitcher:

For a first test use something like this, should be simliar with zenith:
 
```
#!/bin/bash

kdialog --msgbox 'TvChannel: '$1''
```

Now you can start your experiments with

```
#!/bin/bash

mplayer dvb://$1
```

Let me know if you can get it working.

P.S.

What's the size of your xmltv.xml file in Mb and how many days do you grab ?

---

### Post by Jose Catre-Vandis on 2008-10-24
Thanks, I'll do some testing on the scripts.

my TVDATA.xml file is currently 3.1Mb - think I have gone for 7 days

---

### Post by lovinglinux on 2008-10-24
> **Monstermagnet said:**
> Processing large xml files becomes very slow, so it's recommend to only load daily files into TvFox.
That's why i haven't implemented that feature and because i'm not interessted what's on tv tomorrow...

Never say never, so maybe i will implement that feature...

This is the major issue for me, since I get the xml file from a distributor with 7 days programming for all local channels (22 Mb). I'm able to strip it down using a tv_grep script, thus removing the programs from channels I don't subscribe, but the output file still has 3,8 Mb and still takes some time to load whenever I change tabs.

In my case I really want to use TVFox to load weekly schedules, so I can setup reminders and forget about using Freeguide, which reminds only if the program is running. Since I use Firefox almost all the time, would be nice to use TVFox as primary EPG/reminder. I also use OnTV gnome applet, which gives me a list of running tv programs and the subsequent schedules. It loads very quickly and also allow to setup reminders, but lacks the ability to browse/remind programs more than 2 shows ahead.

Additionally, I'm still having issues with cookies. TVFox does not remember my settings, no matter what I do.

---

### Post by Jose Catre-Vandis on 2008-10-24
Working on the extension scripts but have a problem, my current TVDATA.xml which lists all the channel info at the top of the file, sets display names with spaces. Thus when clicking on any BBC channel, e.g. BBC Two, i only get BBc returned from $1.

Can I edit the TVDATA.xml file (which is the same file that gets updated by the cron job) to remove the spaces in the display name?

Like so:

Original:
```
<tv source-info-name="Radio Times" generator-info-name="XMLTV" generator-info-url="http://xmltv.org/wiki/">
  <channel id="bbc1.bbc.co.uk">
    <display-name>BBC One Generic</display-name>
    <icon src="http://www.lyngsat-logo.com/logo/tv/bb/bbc1.jpg" />
  </channel>
```

Would like:
```
<tv source-info-name="Radio Times" generator-info-name="XMLTV" generator-info-url="http://xmltv.org/wiki/">
  <channel id="bbc1.bbc.co.uk">
    <display-name>BBC1</display-name>
    <icon src="http://www.lyngsat-logo.com/logo/tv/bb/bbc1.jpg" />
  </channel>
```

EDIT:

Updating the TVDATA.xml file overwrites any edits to the display name :(

Having played about a bit more, seems the alternate view provides the channel id which has no spaces and is distinct. I changed the xsl file at line 85 to choose the channel id instead of the display name for the main view.
```
       <img class="logo"
             alt="{display-name}"
             src="logo/{display-name}.gif"
             title="{display-name}"
             id="{@id}" />
```

---

### Post by Jose Catre-Vandis on 2008-10-25
Here is my channel switcher script (not all channels included yet) using mplayer and bash
> #!/bin/bash

## grab channel info from mouse click on TvFox

channel=$1

##find which channel for mplayer use

if 
[ "$channel" = "bbc1.bbc.co.uk" ]; 
then
select=BBC1
elif 
[ "$channel" = "bbc2.bbc.co.uk" ]; 
then
select=BBC2
elif 
[ "$channel" = "meridian.itv1.itv.co.uk" ]; 
then
select=ITV1
else

## exits if no correct channel selected for whatever reason, and tells you 

zenity --info \
--text="No Channel Selected!"
exit
fi

## info about channel selection (can be omitted if preferred)

zenity  --question --title="TV Channel Player" --text="         TV Channel:        $select         "


##if not correct channel is chosen for some reason, or user wishes to cancel

myquit=$?
if [ "$myquit" = 1 ]; 
then
zenity --info \
--text="No Channel Selected!"
exit
fi

## for channel switching, need to kill existing mplayer session

killall 9 mplayer

## run mplayer with correct channel, with menu and picture size options

mplayer dvb://$select -menu -xy 0.25

On to the recording script now :)

---

### Post by Monstermagnet on 2008-10-27
@Jose Catre-Vandis

> Working on the extension scripts but have a problem, my current TVDATA.xml which lists all the channel info at the top of the file, sets display names with spaces. Thus when clicking on any BBC channel, e.g. BBC Two, i only get BBc returned from $1.

Put some quotes around it:

```
#!/bin/bash

zenity --info --text \
'Channel: '"$1" \
--title 'Channelswitcher parameters'
```

@lovinglinux

> Additionally, I'm still having issues with cookies. TVFox does not remember my settings, no matter what I do. 

Since you have so many extensions running and tweaked firefox in so many ways, the best solution would be to download a orginal firefox, setup a new profile and run the firefox binary.

- Download the firefox binary at [http://www.mozilla.com]("http://www.mozilla.com")
- Close firefox
- Terminal --> firefox -ProfileManager
- Create new profile "Test"
- Extract
- Terminal --> /home/YOURNAME/Desktop/firefox/firefox -P "Test" (Edit to your path)
- In that firefox instance --> goto File --> open File --> path to TvFox.html

Please let me know if that works.

About the speed issues, javascript is slow ...

My daily xmltv output is around 500 Kb with 60 channels and that's processing fast enough.

So the only solution is to shrink down the file size.

I have some ideas to improve the speed, but "the real life strikes back..."

---

### Post by Jose Catre-Vandis on 2008-10-27
What are the variables emitted by TvFox for recording?

In your mencoder.py script you indicate 8 sys argv 's

```
channelId = sys.argv[1]

year = sys.argv[2]
month = sys.argv[3]
day = sys.argv[4]
hour = sys.argv[5]
minute = sys.argv[6]

title = sys.argv[7]

duration = sys.argv[8]
```

so do i take these to be:

$1 = channelId = sys.argv[1]
$2 = year = sys.argv[2]
$3 = month = sys.argv[3]
$4 = day = sys.argv[4]
$5 = hour = sys.argv[5]
$6 = minute = sys.argv[6]
$7 = title = sys.argv[7]
$8 = duration = sys.argv[8]

and that TvFox emits these when you click on the Record item in the right click menu?

---

### Post by Monstermagnet on 2008-10-28
```
#!/bin/bash

zenity --info --text \
'Channel: '"$1"'\n
Start year: '$2'\n
Start month: '$3'\n
Start day: '$4'\n
Start hour: '$5'\n
Start minute: '$6'\n
Title: '"$7"'\n
Duration: '$8 \
--title 'Recording parameters'
```

Updated to TvFox_0.2.1

Added some examples.

---

### Post by Jose Catre-Vandis on 2008-10-28
Cool. I notice you cannot start recording an "already started" programme, for obvious reasons given the output. Is there a way to turn this off so it is possible to start a recording? (obviously one would have to script around the start time being in the past anbd adjust the duration, but I enjoy doing that bit!)

---

### Post by ianhaycox on 2008-10-28
Instead of copying my XML file I created a link,

```

ln -s ../.xmltv/tvguide.xml TVDATA.xml

```

to my existing EPG data generated by MaxemumTvGuide and TvFox didn't display any listings. Once I actually copied the file it worked a treat.

Thanks, a nice addition. Maybe I can get rid of my only KDE app.

---

### Post by Monstermagnet on 2008-10-28
@Jose Catre-Vandis

Maybe another contextmenu item Timeshift would make sense ?

So if a program is running, we run a PVR script like the one lovinglinux posted ? ( BTW: Very cool ! )

[http://ubuntuforums.org/showthread.php?p=5748047]("http://ubuntuforums.org/showthread.php?p=5748047")

So only the channel, the title and the duration are send as parameters, because we don't need a cronjob here.

I love that idea.

Will be implemented in the next version...

@ianhaycox

> Instead of copying my XML file I created a link,

Sorry, but this will not work.

---

### Post by Jose Catre-Vandis on 2008-10-28
> **Monstermagnet said:**
> 
So only the channel, the title and the duration are send as parameters, because we don't need a cronjob here.


Could it collect the start hour and minute as well, when you create the new context item?

---

### Post by Monstermagnet on 2008-10-29
> Could it collect the start hour and minute as well

Rec start time of running programs is NOW.

---

### Post by Monstermagnet on 2008-11-21
Hello,

a new version is out, please visit [http://tvfox.bplaced.net/]("http://tvfox.bplaced.net/")

Version 0.5 :

    * 21 November 2008
    * Added default settings file
    * New default theme
    * Added spincontrols for reminders and recordings
    * Reminders open as popup windows
    * Choise of different recording qualities
    * Alarmtime is shown in Remindertab
    * Small bugfixes
    * TvFoxEx updated to version 0.8
    * Website: Completly redesigned
    * TODO: FIX tv_grab_eu_epgdata multiple categories (PRIORITY: LOW)
    * TODO: Improve performance ...(loading different xml files per date will be the first step (will require: xmltv tv_split --output %Y%m%d.xml)) (PRIORITY: HIGH)
    * TODO: Show TV programs by date (PRIORITY: MIDDLE)
    * TODO: Another gridview (PRIORITY: VERY LOW)
    * TODO: TvFoxEx for website use (PRIORITY: LOW)
    * TODO: Suggestions welcome...

---

### Post by Monstermagnet on 2008-11-22
New Bugfix release

Version 0.5.1 :

    * 22 November 2008
    * Fixed bug in autoselect and sort network (boolean value is now string)

[http://tvfox.bplaced.net]("http://tvfox.bplaced.net")

---

### Post by Monstermagnet on 2008-12-02
Hello,

a new version is out, please visit [http://tvfox.bplaced.net/]("http://tvfox.bplaced.net/")

Version 0.6 :

    * 2 December 2008
    * Improved performance !
    * Removed Settings tab !
    * Removed Listview !
    * Removed Splashscreen !
    * New settings file !
    * TODO: Suggestions welcome...

---

### Post by lovinglinux on 2008-12-02
> **Monstermagnet said:**
> Hello,

a new version is out, please visit [http://tvfox.bplaced.net/]("http://tvfox.bplaced.net/")

Version 0.6 :

    * 2 December 2008
    * Improved performance !
    * Removed Settings tab !
    * Removed Listview !
    * Removed Splashscreen !
    * New settings file !
    * TODO: Suggestions welcome...

Thanks for the update.

I no longer have issues with cookies since version 5.1.

I would like to suggest to modify the layout. I don't know how hard would be to make such changes, but would be nice if the show description pops up with java or something instead of being displayed in the bottom of the screen. Alternatively, you could put it on a panel in the right of the screen. This way, the grid scroll bar could fill the entire screen height. I feel that the current grid area is too small. Just my 2 cents.

---

### Post by Monstermagnet on 2008-12-02
Hello,

thanks for yor feedback.

i played around with the gui, especially with a new time and not yet implemented date picker, but i don't liked none of them. Maybe you have an idea. If so, a simple Mock-up would be cool.

> I don't know how hard would be to make such changes, but would be nice if the show description pops up with java or something instead of being displayed in the bottom of the screen.

I will think about it, maybe make it an option.

> Alternatively, you could put it on a panel in the right of the screen. This way, the grid scroll bar could fill the entire screen height.

This can be done with another theme file: --> next version

BTW: Could you please post your xml file to pastebin.com or if that reaches the limit to File-Upload.net/rapidshare.com, so i can have a look at it.

---

### Post by lovinglinux on 2008-12-02
Do you want the original xml file (22 Mb) or the filtered version (4 Mb)?

---

### Post by Monstermagnet on 2008-12-03
If it's not a problem for you the large one.

Thanks

---

### Post by lovinglinux on 2008-12-03
I attached the file as a zip, but you need to remove the zip extension to extract it, because it's actually a 7z file.

---

### Post by Monstermagnet on 2008-12-03
Hello,

a new version is out, please visit [http://tvfox.bplaced.net/](http://tvfox.bplaced.net/)

Version 0.6.1 :

    * 3 December 2008
    * New Theme "VerticalGreen"
    * TODO: FIX multiple categories 
    * TODO: Suggestions welcome...

@lovinglinux

Thanks for posting your xmltv.xml file.
The new version contains a new theme "VerticalGreen".

1. Wow that's compression 20MB to 800kb, never tried that...

2. AAAAARRRGH you also have multiple categories in there (thats why categories wont work for you), i will look into it (will take some time...)

3. I changed my timezone to brazil -300 before i splitted your file with xmlt tv_splitt but the result was TIMEZONE -200 and there was no show after 21:00, i hope that you have more luck with xmltv tv_splitt.

4.If you want to create your own theme:

open /themes/YOURFAVORITETHEME/YOURFAVORITETHEME.css in your favorite editor.

Start with changeing some images or colors.

This is would be the simplest theme:

body
{
	background-color: green;
}

If you want to create a completly different theme and only then:

open /css/TvFox.css (Please do not edit TvFox.css !!!)

TvFox.css contains all available elements, a theme css can add element properties or change them.

If you want to change properties that are allready defined in TvFox.css simply define them again.

In TvFox.css

/*Pages (the main containers)*/
div.pageX
{
	position: absolute;
	top: 90px;
	bottom: 140px;
	left: 4%;
	right: 4%;
}

YOURNEWTHEME.css

/*Pages (the main containers)*/
div.pageX
{
	position: absolute;
	top: 180px;
	bottom: 140px;
	left: 20%;
	right: 20%;
	background-color: black;
	padding : 20px;
}

If you made something new, please post it here.

Thanks again for your feedback.

---

### Post by lovinglinux on 2008-12-03
> **Monstermagnet said:**
> 
@lovinglinux

Thanks for posting your xmltv.xml file.
The new version contains a new theme "VerticalGreen".

1. Wow that's compression 20MB to 800kb, never tried that...

Cool. I will download it now. Thanks a lot for the new vertical theme.

A simple zip compression would shrink the file to 1.4 mb, so I expected to get less than that with 7z. If I compressed it with lzma then the size would be something like 400 Kb , but I can't extract lzma to test it :)

> **Monstermagnet said:**
> 2. AAAAARRRGH you also have multiple categories in there (thats why categories wont work for you), i will look into it (will take some time...)

Last time I checked, Categories was working.

> **Monstermagnet said:**
> 3. I changed my timezone to brazil -300 before i splitted your file with xmlt tv_splitt but the result was TIMEZONE -200 and there was no show after 21:00, i hope that you have more luck with xmltv tv_splitt.

I never used tv_splitt, but I guess is to divide the xmltv file into daily files right?

I don't think I would need that. The newer versions of TvFox are much faster and I clean up the unnecessary schedules and channels with the script below.

```
tv_grep --output ~/databases/xmltv/xmltv.xml --channel "HBO|HB2|HPL|HPE|MAP|MPE|MAX|MXE|HFA|HFE|TNT|TCM|SET|WBT|FOX|FLI|MDO|TRA|EET|DNY|DIS|SUP|BAN|REC|RTV|SBT" ~/temp/xmltv.xml

cat ~/databases/xmltv/xmltv.xml | sed -e '/id=\"100\"/,+2d' -e '/id=\"121\"/,+2d' -e '/id=\"135\"/,+2d' -e '/id=\"ADM\"/,+2d' -e '/id=\"AGS\"/,+2d' -e '/id=\"AMZ\"/,+2d' -e '/id=\"APL\"/,+2d' -e '/id=\"ART\"/,+2d' -e '/id=\"AT3\"/,+2d' -e '/id=\"ASL\"/,+2d' -e '/id=\"100\"/,+2d' -e '/id=\"BBC\"/,+2d' -e '/id=\"BIT\"/,+2d' -e '/id=\"BIO\"/,+2d' -e '/id=\"BMG\"/,+2d' -e '/id=\"BOI\"/,+2d' -e '/id=\"BPO\"/,+2d' -e '/id=\"BRA\"/,+2d' -e '/id=\"BSP\"/,+2d' -e '/id=\"BUT\"/,+2d' -e '/id=\"C21\"/,+2d' -e '/id=\"CAM\"/,+2d' -e '/id=\"CAR\"/,+2d' -e '/id=\"CBR\"/,+2d' -e '/id=\"CBS\"/,+2d' -e '/id=\"100\"/,+2d' -e '/id=\"CCL\"/,+2d' -e '/id=\"CFX\"/,+2d' -e '/id=\"CLI\"/,+2d' -e '/id=\"100\"/,+2d' -e '/id=\"CNE\"/,+2d' -e '/id=\"CNN\"/,+2d' -e '/id=\"CNT\"/,+2d' -e '/id=\"CNV\"/,+2d' -e '/id=\"CUL\"/,+2d' -e '/id=\"DCI\"/,+2d' -e '/id=\"DIK\"/,+2d' -e '/id=\"DSC\"/,+2d' -e '/id=\"DTU\"/,+2d' -e '/id=\"DWL\"/,+2d' -e '/id=\"100\"/,+2d' -e '/id=\"ESB\"/,+2d' -e '/id=\"ESC\"/,+2d' -e '/id=\"ESP\"/,+2d' -e '/id=\"EUR\"/,+2d' -e '/id=\"100\"/,+2d' -e '/id=\"FAS\"/,+2d' -e '/id=\"FIZ\"/,+2d' -e '/id=\"FNE\"/,+2d' -e '/id=\"FUT\"/,+2d' -e '/id=\"GAZ\"/,+2d' -e '/id=\"GBB\"/,+2d' -e '/id=\"GBG\"/,+2d' -e '/id=\"GBM\"/,+2d' -e '/id=\"GHD\"/,+2d' -e '/id=\"GLN\"/,+2d' -e '/id=\"GLS\"/,+2d' -e '/id=\"GNT\"/,+2d' -e '/id=\"GRC\"/,+2d' -e '/id=\"GRD\"/,+2d' -e '/id=\"GRJ\"/,+2d' -e '/id=\"GSP\"/,+2d' -e '/id=\"GVA\"/,+2d' -e '/id=\"HAL\"/,+2d' -e '/id=\"HBE\"/,+2d' -e '/id=\"HEA\"/,+2d' -e '/id=\"HEC\"/,+2d' -e '/id=\"HIS\"/,+2d' -e '/id=\"HOT\"/,+2d' -e '/id=\"HSE\"/,+2d' -e '/id=\"HTV\"/,+2d' -e '/id=\"IDL\"/,+2d' -e '/id=\"INF\"/,+2d' -e '/id=\"JUS\"/,+2d' -e '/id=\"KID\"/,+2d' -e '/id=\"LBV\"/,+2d' -e '/id=\"LOC\"/,+2d' -e '/id=\"MGM\"/,+2d' -e '/id=\"MIX\"/,+2d' -e '/id=\"MSW\"/,+2d' -e '/id=\"MTH\"/,+2d' -e '/id=\"MTJ\"/,+2d' -e '/id=\"MTV\"/,+2d' -e '/id=\"NAC\"/,+2d' -e '/id=\"NBR\"/,+2d' -e '/id=\"NEW\"/,+2d' -e '/id=\"NHK\"/,+2d' -e '/id=\"NIC\"/,+2d' -e '/id=\"NGT\"/,+2d' -e '/id=\"NSC\"/,+2d' -e '/id=\"PLA\"/,+2d' -e '/id=\"POA\"/,+2d' -e '/id=\"PV1\"/,+2d' -e '/id=\"PV2\"/,+2d' -e '/id=\"PV3\"/,+2d' -e '/id=\"PV4\"/,+2d' -e '/id=\"PV5\"/,+2d' -e '/id=\"PV6\"/,+2d' -e '/id=\"PV7\"/,+2d' -e '/id=\"PV8\"/,+2d' -e '/id=\"PV9\"/,+2d' -e '/id=\"P10\"/,+2d' -e '/id=\"P11\"/,+2d' -e '/id=\"P12\"/,+2d' -e '/id=\"RAI\"/,+2d' -e '/id=\"RCN\"/,+2d' -e '/id=\"REF\"/,+2d' -e '/id=\"RIT\"/,+2d' -e '/id=\"RTB\"/,+2d' -e '/id=\"RTP\"/,+2d' -e '/id=\"RUR\"/,+2d' -e '/id=\"SEN\"/,+2d' -e '/id=\"SPE\"/,+2d' -e '/id=\"SHO\"/,+2d' -e '/id=\"SIC\"/,+2d' -e '/id=\"SP2\"/,+2d' -e '/id=\"SPO\"/,+2d' -e '/id=\"SRD\"/,+2d' -e '/id=\"STC\"/,+2d' -e '/id=\"TBC\"/,+2d' -e '/id=\"TC1\"/,+2d' -e '/id=\"TC2\"/,+2d' -e '/id=\"TC3\"/,+2d' -e '/id=\"TC4\"/,+2d' -e '/id=\"TC5\"/,+2d' -e '/id=\"TED\"/,+2d' -e '/id=\"TGC\"/,+2d' -e '/id=\"THF\"/,+2d' -e '/id=\"TRW\"/,+2d' -e '/id=\"TV5\"/,+2d' -e '/id=\"TVV\"/,+2d' -e '/id=\"TVE\"/,+2d' -e '/id=\"TVU\"/,+2d' -e '/id=\"UNO\"/,+2d' -e '/id=\"USA\"/,+2d' -e '/id=\"VDA\"/,+2d' -e '/id=\"VH1\"/,+2d' -e '/id=\"VHS\"/,+2d' -e '/id=\"WNT\"/,+2d' -e '/id=\"XTV\"/,+2d' -e '/id=\"WOO\"/,+2d' -e '/id=\"CAD\"/,+2d' -e '/id=\"TVT\"/,+2d' -e '/id=\"772\"/,+2d' -e '/id=\"774\"/,+2d' -e '/id=\"COR\"/,+2d' -e '/id=\"PLS\"/,+2d' -e '/id=\"MPX\"/,+2d' -e '/id=\"SCI\"/,+2d' -e '/id=\"PHD\"/,+2d' -e '/id=\"TC1\"/,+2d' -e '/id=\"TLS\"/,+2d' -e '/id=\"TRV\"/,+2d' -e 's/www.revistaeletronica.com.br//g' -e 's/TCM - Turner Classic Movies/TCM/g' -e 's/Sony Entertainment Television/Sony/g' -e 's/E! Entertainment Television/E!/g'> ~/databases/xmltv/list.xmltv
```

The resulting file has only 4.1 Mb


> **Monstermagnet said:**
> 4.If you want to create your own theme:

open /themes/YOURFAVORITETHEME/YOURFAVORITETHEME.css in your favorite editor.

Start with changeing some images or colors.

This is would be the simplest theme:

body
{
	background-color: green;
}

If you want to create a completly different theme and only then:

open /css/TvFox.css (Please do not edit TvFox.css !!!)

TvFox.css contains all available elements, a theme css can add element properties or change them.

If you want to change properties that are allready defined in TvFox.css simply define them again.

In TvFox.css

/*Pages (the main containers)*/
div.pageX
{
	position: absolute;
	top: 90px;
	bottom: 140px;
	left: 4%;
	right: 4%;
}

YOURNEWTHEME.css

/*Pages (the main containers)*/
div.pageX
{
	position: absolute;
	top: 180px;
	bottom: 140px;
	left: 20%;
	right: 20%;
	background-color: black;
	padding : 20px;
}

If you made something new, please post it here.

Thanks again for your feedback
 
Thanks. I will try to make a theme and will post it here if I get something decent :)

BTW, how do I translate TvFox? I forgot about translating it into Portuguese, because I do prefer to use all my softwares in English. It's easier to follow tutorials and posts from the community in the same language of the applications.

---

### Post by Monstermagnet on 2008-12-03
> Last time I checked, Categories was working.

Could you please post that file where categories was working for you ?

> BTW, how do I translate TvFox? I forgot about translating it into Portuguese, because I do prefer to use all my softwares in English. It's easier to follow tutorials and posts from the community in the same language of the applications.

Would be nice to see a new language in TvFox:

open /i18n/TvFoxLocales.js and add "pt", please take care of the comma separated values.

```
var TvFoxLocales =
{
	'en':
	{
		'tab1Label' : 'Tv Guide'
	},
	'de':
	{
		'tab1Label' : 'Tv Programm'
	},
	'pt':
	{
		'tab1Label' : 'Guia de TV'
	}
};

```
Guia de TV ???, i hope that this translation is correct.

---

### Post by lovinglinux on 2008-12-03
> **Monstermagnet said:**
> Could you please post that file where categories was working for you ?

Attached!


> **Monstermagnet said:**
> Would be nice to see a new language in TvFox:
Guia de TV ???, i hope that this translation is correct.

Yep, that is correct ;)

Here is the translation.

```
	'pt-BR':
	{
		'tab1Label' : 'Guia de TV',
		'tab2Label' : 'Categorias',
		'tab3Label' : 'Favoritos',
		'tab4Label' : 'Lembretes',
		'tab5Label' : 'Temas',
		'tab6Label' : 'Configurações',
		'button1Label' : 'Agora',
		'button2Label' : 'Nobre',
		'button3Label' : 'Categorias favoritas',
		'button4Label' : 'Adicionar categoria',
		'button5Label' : 'Apagar categoria',
		'mouseover1Label' : 'Clique para apagar favorito',
		'contextMenu1Label' : 'Minha busca',
		'contextMenu2Label' : 'Busca IMDB',
		'contextMenu3Label' : 'Busca Google',
		'contextMenu4Label' : 'Adicionar lembrete',
		'contextMenu5Label' : 'Adicionar aos favoritos',
		'contextMenu6Label' : 'Gravar',
		'contextMenu7Label' : 'Lembrete do sistema',
		'infoBox1Label' : 'Programa no ar!',
		'infoBox2Label' : 'Gravando',
		'infoBox3Label' : 'Iniciar gravação as:',
		'infoBox4Label' : 'Parar gravação as:',
		'infoBox5Label' : 'Confirmar gravação',
		'infoBox6Label' : 'Duração:',
		'infoBox7Label' : 'minutos',
		'infoBox8Label' : 'Adicionar lembrete ?',
		'infoBox9Label' : 'Lembrete TvFox !',
		'infoBox10Label' : 'Configurar lembrete do sistema ?',
		'infoBox11Label' : 'Apagar favorito ?',
		'infoBox12Label' : 'Já é favorito:',
		'infoBox13Label' : 'Adicionar favorito ?',
		'infoBox14Label' : 'Já é categoria favorita:',
		'infoBox15Label' : 'Adicionar categoria ?',
		'infoBox16Label' : 'Nenhuma categoria selecionada !',
		'infoBox17Label' : 'Apagar categoria ?',
		'infoBox18Label' : 'Nenhuma categoria favorita !',
		'infoBox19Label' : 'Canal:',
		'infoBox20Label' : 'Título:',
		'infoBox21Label' : 'Início:',
		'infoBox22Label' : 'Categorias selecionadas automaticamente não podem ser marcadas como favoritas !',
		'infoBoxButton1Label' : 'Cancelar',
		'infoBoxButton2Label' : 'Fechar',
		'infoBoxButton3Label' : 'Gravar',
		'infoBoxButton4Label' : 'OK'
	}
```

I have modified the DarkBlue theme. This is what I got so far:

[[IMG]http://img389.imageshack.us/img389/7360/screenshottvfoxmozillafdz8.th.png[/IMG]](http://img389.imageshack.us/img389/7360/screenshottvfoxmozillafdz8.png)

[[IMG]http://img389.imageshack.us/img389/3382/screenshottvfoxmozillafdx9.th.png[/IMG]](http://img389.imageshack.us/img389/3382/screenshottvfoxmozillafdx9.png)

[[IMG]http://img20.imageshack.us/img20/2326/screenshottvfoxmozillafhq5.th.png[/IMG]](http://img20.imageshack.us/img20/2326/screenshottvfoxmozillafhq5.png)

[[IMG]http://img361.imageshack.us/img361/7787/screenshottvfoxmozillaflt5.th.png[/IMG]](http://img361.imageshack.us/img361/7787/screenshottvfoxmozillaflt5.png)

[[IMG]http://img20.imageshack.us/img20/4779/screenshottvfoxmozillafdp0.th.png[/IMG]](http://img20.imageshack.us/img20/4779/screenshottvfoxmozillafdp0.png)

The only issue I have with this theme is that I had to remove the text labels from the menu in the TVFox.html file. I tried to make it vertical, but when I add columns to the table the menu doesn't work.

I also tried to use the tv_splitt command, but got the same result as you did. The only issue I see about using the complete xmltv file is the cpu overload and time required to process the file when accessing the Categories. The rest of the features works just fine.

There is another thing that I feel is not right in my installation. There are no icons for the context menu. I have to click several times with the right mouse button to make it show up and I really don't know the exact place to click.

Since you removed the settings tab, how do I enable the recording feature?

---

### Post by Monstermagnet on 2008-12-04
Hello,

a new version is out, please visit [http://tvfox.bplaced.net/](http://tvfox.bplaced.net/)

Version 0.6.2 :

    * 4 December 2008
    * Added portuguese translation by lovinglinux (Many thanks !)
    * TODO: Suggestions welcome...

@lovinglinux

WOW, that is awesome ! :popcorn:

I don't see any problems not using labels, the icons should be selfexplaining enough.

If you need to make any changes to make your theme work, please feel free to do so.

Just send me the complete TvFox package instead of only the theme, and i will include your modified code.

Can't wait to see your theme in action.

> Here is the translation.

Many thanks !

> There is another thing that I feel is not right in my installation. There are no icons for the context menu.

No icons ?

I don't know how to solve that.

> I have to click several times with the right mouse button to make it show up and I really don't know the exact place to click.

The contextmenu will only show up if you rightclick on a cell that contains a program title.

> Since you removed the settings tab, how do I enable the recording feature?

There is now a settings file in the main directory:

/*Show contextmenu item "Systemreminder": Boolean: true, false*/
  showsystemreminderincontextmenu : false,
/*Show contextmenu item "Record": Boolean: true, false*/
  showrecordincontextmenu : true

Please make shure that TvFoxEx version 0.8 is installed.

And again many thanks for your help ! ):P

---

### Post by lovinglinux on 2008-12-04
> **Monstermagnet said:**
>  * Added portuguese translation by lovinglinux (Many thanks !)

You are welcome.

> **Monstermagnet said:**
> @lovinglinux

WOW, that is awesome ! :popcorn:

I don't see any problems not using labels, the icons should be selfexplaining enough.

If you need to make any changes to make your theme work, please feel free to do so.

Just send me the complete TvFox package instead of only the theme, and i will include your modified code.

Can't wait to see your theme in action.

I will make sure it works properly on widescreen monitors (mine is 4:3) and then I will send it to you.

> **Monstermagnet said:**
> No icons ?

I don't know how to solve that.

The contextmenu will only show up if you rightclick on a cell that contains a program title.

Actually, the icons are displayed in the context menu. The problem is where to click to display the context menu. There is no icon for that and clicking on a cell seems to have erratic results. Sometimes it does show up, sometimes it doesn't. For me is not actually a serious issue, but I'm considering using it on other computers in my local network and I'm the only geek here :)

> **Monstermagnet said:**
> There is now a settings file in the main directory:

/*Show contextmenu item "Systemreminder": Boolean: true, false*/
  showsystemreminderincontextmenu : false,
/*Show contextmenu item "Record": Boolean: true, false*/
  showrecordincontextmenu : true

Please make shure that TvFoxEx version 0.8 is installed.

And again many thanks for your help ! ):P

Thank you. I'm glad I can help you with this great project. I wouldn't have the skills to make it, but I can imagine all the hard work you put into it.

---

### Post by lovinglinux on 2008-12-04
> **lovinglinux said:**
> Actually, the icons are displayed in the context menu. The problem is where to click to display the context menu. There is no icon for that and clicking on a cell seems to have erratic results. Sometimes it does show up, sometimes it doesn't. For me is not actually a serious issue, but I'm considering using it on other computers in my local network and I'm the only geek here :)

EDIT: I figured it out. This p&#341;oblem is caused by easystroke application. Once I quit it, it works flawlessly.

---

### Post by lovinglinux on 2008-12-05
I have updated my Firefox Media Center tutorial to include TvFox integration. So now I can schedule recordings manually, by e-mail or using the TvFox grid.

It works like a charm! 

Thanks again for this awesome application.

BTW, I have a little update to make in the Settings.js pt section.

```

  'pt':
  {
    'recquality1' : 'Qualidade Baixa',
    'recquality2' : 'Qualidade Alta',
    'recquality3' : 'Em tempo real'
  }
```

---

### Post by Monstermagnet on 2008-12-05
Hello,

a new version is out, please visit [http://tvfox.bplaced.net/](http://tvfox.bplaced.net/)

Version 0.7 :

    * 5 December 2008
    * Better support for categories
    * TODO: Suggestions welcome...

@lovinglinux

> I figured it out. This problem is caused by easystroke application. Once I quit it, it works flawlessly.

Glad that it works now as expected.

> BTW, I have a little update to make in the Settings.js pt section.

Thanks

---

### Post by lovinglinux on 2008-12-05
> **Monstermagnet said:**
> Version 0.7 :

    * 5 December 2008
    * Better support for categories

w00t

This update was amazing. The Categories feature is now loading in just a few seconds! Thank you.

> **Monstermagnet said:**
> 
    * TODO: Suggestions welcome...

I have another TODO suggestion :)

Would be possible to port the TvFoxEx to Prism?

I'm testing my new theme with Prism and it looks pretty nice, because I don't have to run Firefox in fullscreen to save space. Unfortunately, when opening with Prism I can't use the recording feature, because the extension is not compatible. I have manage to install it by changing the "install.rdf" file, but it doesn't work.

You can find some info about Prism extensions [**here**]("https://developer.mozilla.org/en/Prism/Extensions")

Here is how my theme looks in Prism:

[[IMG]http://img68.imageshack.us/img68/2770/screenshottvfoxzk5.th.png[/IMG]](http://img68.imageshack.us/img68/2770/screenshottvfoxzk5.png)

---

### Post by Monstermagnet on 2008-12-07
I had a look at prism and i was not very satisfied, so i decided to make TvFox a xulrunner application.

I already have a working app, but it will take a while to get it ready.

Please stay tuned.

---

### Post by lovinglinux on 2008-12-07
> **Monstermagnet said:**
> I had a look at prism and i was not very satisfied, so i decided to make TvFox a xulrunner application.

I already have a working app, but it will take a while to get it ready.

Please stay tuned.

That's cool. Thank you.

I  don't know how xulrunner application would be implemented, but if it also use cookies for storing reminders and favorites, would be nice to have an option in TVFoxEx to set the path to "cookies.sqlite" database. This way, would be possible to open TVFox on Firefox or xulrunner, using the same shared data. This is not so important, but could give the users the option to use one or the other without making them completely separate applications.

Another topic:

I have implemented a system reminder script that allow to store reminders in a Google Calendar account. 

To  implement this, we need to install gcalcli first, by following [[COLOR="Red"]**this nice tutorial**[/COLOR]]("http://blog.wired.com/monkeybites/2007/10/how-to-embed-go.html"). Then create a reminder script with the following code and add it's path to TVFoxEx:

```
gcalcli quick ''$2'-'$3'-'$4' '$5':'$6' TV Reminder'
```

We also need to setup the Calendar with a default reminder, otherwise it will not send any reminders, just list the appointments.

It works pretty fine, but there are a couple of issues.

The Google Calendar must be using English as interface language, otherwise it will store the reminder in the wrong format. This is a gcalcli issue.

Additionally, I can't make the title of the reminder to work properly using the TVFox variable. If the title is a single word it works fine, but when the title contain multiple words and spaces, it screw up the reminder.

Please notice in my code that all reminders will be titled as "TV Reminder" and there is a space in it. Which is weird, because when I use the variable for the title, it only works when there isn't any spaces on it. Maybe I should put a quote somewhere else, but I can't figure it out.

---

### Post by lovinglinux on 2008-12-07
Hi Monstermagnet,

Since I saw your post about xulrunner as an alternative for launching TvFox with Prism, I couldn't hold my curiosity and searched for a few xulrunner tutorials.

I have already created a simple xul application with TvFox inside. Obviously not working properly, because of the cookies. Anyway, here is the screenshot.

[[IMG]http://img123.imageshack.us/img123/8476/screenshotxulmediacentezl0.th.png[/IMG]](http://img123.imageshack.us/img123/8476/screenshotxulmediacentezl0.png)

I don't know if the cookie issue is because of xulrunner not saving any cookies or because of my cookie issues coming back to haunt me.

Anyway, then I realized there is a simpler way of making it open like Prism or like a xulrunner application. All I had to do was modify the tvfoxex.js file in the TvFoxEx extension, to launch a new window without toolbars.

Here is the code that I have changed:

```

startTvFox:  function () {
    if (TvFoxEx.url.search("TvFox") > -1) {
    window.open("file://localhost" + TvFoxEx.url + "", "", "url,width=1024,height=768"); 
    }
  }
```

So now it works perfectly.

---

### Post by Monstermagnet on 2008-12-08
Good to see that you found a solution for you, anyway here's a prism extension.

Works with:
Mozilla Prism 0.9 (Thanks Wladimir Palant (Adblock Plus) for posting the [_workaround_]("https://bugzilla.mozilla.org/show_bug.cgi?id=465991")
and 
[_Mozilla Prism 0.9.1 (Experimental)_]("http://browsing.justdiscourse.com/2008/07/10/mozilla-prism-091-experimental-now-available/")

Both versions of prism have a bug:

0.9 has a layout bug
0.9.1 doesn't allow links

but anyway here you go:

[_TvFoxPrism_0.1.xpi_]("http://tvfox.bplaced.net/TvFoxPrism_0.1.xpi") (save link as)

BTW: 

Which category selection do you use ?

```
/*If your xmltv contains more than one category per tv show you can choose how they will be listed
(just try what you like most) : Number: 1 or 2*/
  categoryselection : 1,
```

---

### Post by lovinglinux on 2008-12-08
> **Monstermagnet said:**
> Good to see that you found a solution for you, anyway here's a prism extension.

Works with:
Mozilla Prism 0.9 (Thanks Wladimir Palant (Adblock Plus) for posting the [_workaround_]("https://bugzilla.mozilla.org/show_bug.cgi?id=465991")
and 
[_Mozilla Prism 0.9.1 (Experimental)_]("http://browsing.justdiscourse.com/2008/07/10/mozilla-prism-091-experimental-now-available/")

Both versions of prism have a bug:

0.9 has a layout bug
0.9.1 doesn't allow links

but anyway here you go:

[_TvFoxPrism_0.1.xpi_]("http://tvfox.bplaced.net/TvFoxPrism_0.1.xpi") (save link as)


Thank you. Unfortunately, I couldn't install it because it keeps saying it's not compatible with Firefox 3.04.


> **Monstermagnet said:**
> 
Which category selection do you use ?

```
/*If your xmltv contains more than one category per tv show you can choose how they will be listed
(just try what you like most) : Number: 1 or 2*/
  categoryselection : 1,
```

I'm using number 1, why?

I was wondering, why you don't include the TvFox code in the TvFoxEx extension?

Wouldn't be possible then to replace the path to TvFox with the path to the xmltv file?

I'm sorry if I'm asking too many development questions here. Please let me know if you wish to discuss this kind of stuff on another place.

---

### Post by Monstermagnet on 2008-12-08
> Thank you. Unfortunately, I couldn't install it because it keeps saying it's not compatible with Firefox 3.04.

It's a prism extension, install it in prism. Please let me know if it works.

> I was wondering, why you don't include the TvFox code in the TvFoxEx extension?

I don't see a reason for this.

> I'm using number 1, why?

Because i will delete this feature in the next version, built in just for testing.

> I'm sorry if I'm asking too many development questions here. Please let me know if you wish to discuss this kind of stuff on another place.

I don't care

---

### Post by lovinglinux on 2008-12-08
> **Monstermagnet said:**
> It's a prism extension, install it in prism. Please let me know if it works.

I'm so stupid :oops: I guess my brain was fried by some xul codes I was trying to make :)

I will test it soon.

> **Monstermagnet said:**
> Because i will delete this feature in the next version, built in just for testing.I don't care

I hope this doesn't mean it will not load fast anymore :(

> **Monstermagnet said:**
> I don't see a reason for this.

IMO, this could facilitate installation and updates. Additionally, it could give more visibility to your project in the Mozilla site. Just my 2 cents.

---

### Post by Monstermagnet on 2009-03-05
Hello,

today i released TvFox 0.9.4 which is now a standalone XULRunner application.

Please visit [http://tvfox.bplaced.net/](http://tvfox.bplaced.net/)

Thanks

---

### Post by lovinglinux on 2009-03-05
> **Monstermagnet said:**
> Hello,

today i released TvFox 0.9.4 which is now a standalone XULRunner application.

Please visit [http://tvfox.bplaced.net/](http://tvfox.bplaced.net/)

Thanks

Nice work!

Did you decided to stay with XulRunner instead of making it a Firefox extension?

---

### Post by Monstermagnet on 2009-03-05
The reason to use XULRunner and not to create a firefox extension is because:

- Security:

TvFox runs in its own process, so we can forget about cross site attacks, it is never a good idea to run a chrome privileged site inside a firefox tab.

- Fullscreen
- Free browser choise
- No conflicts with other extensions

Thanks for your interest :)

---

### Post by Monstermagnet on 2009-04-05
Hello,

a new version is out, please visit [http://tvfox.bplaced.net/](http://tvfox.bplaced.net/)

Version 1.0.2 :

5 April 2009

Fixed description overflow bug
Improved CSS
Added CSS text ellipsis hack
Added recording tab
Simplified recordings, no need for external AT tools
Removed system reminders
Improved notification dialog
New theme: Oxygenic :-)

---

### Post by Monstermagnet on 2009-04-19
Hello,

a new version is out, please visit [http://tvfox.bplaced.net/](http://tvfox.bplaced.net/)

Version 1.0.3 :

19 April 2009

Added Zapping and recording examples
Settings: Directories will open at the desired location
Theme Oxygenic: added contextmenu gradients
Added portuguese translation by Ediglei (Many thanks !)
Seperate downloads for Linux and MS Windows (to preserve file permissions)
Website Installguide: screenshots added

---

### Post by Jose Catre-Vandis on 2009-04-22
Now TVFox is an xulrunner application, how do I sort the channels as per the xmltv sort? (See my previous post about the non xulrunner version)

---

### Post by Monstermagnet on 2009-04-23
Hello,

that's pretty simple, just uncheck "sort networks alphabetically".

Since you are a native english speaker maybe you wanna help me which the translation ?

You can find the translation file at my forum.

BTW: A new version is coming soon !

---

### Post by Jose Catre-Vandis on 2009-04-24
I thought I did, and TvFox didn't! :) I'll go check.

---

### Post by Jose Catre-Vandis on 2009-04-25
I did. But xmltv is not sorting how I want to, so had to sort the channels out manually. Fingers crossed I don't have to do this every week :) Looking good now :)

[ATTACH]111028[/ATTACH]

---

### Post by Monstermagnet on 2009-04-26
I will add custom channel sorting in a future version.

---

### Post by Jose Catre-Vandis on 2009-04-26
It only takes a minute or so in the grabber conf file.

One issue, having to use the vertical green skin, because for all the horizontal skins, if there is a lot of accompanying text, it disappears off the bottom of the window, with no way of reading it. Didn't happen in previous non xulrunner version.

---

### Post by Monstermagnet on 2009-04-26
This feature was removed.
But it will be back when keyboard navigation is ready.

---

### Post by Monstermagnet on 2009-06-23
Hello,

a new version is out, please visit [http://tvfox.bplaced.net/](http://tvfox.bplaced.net/)

Version 1.5.1 :

23 June 2009

-Added statusbar (--> toolbar)
-Moved settings- and themetab to toolbar
-Added zoom and fullscreen
-Added custom background image
-Added show descriptions only on mouseclick
-Added custom number of colums in tvguide
-Added reload button
-Added spincontrols in settingstab
-Improved firststart windowsize
-All themes updated
-Small Bugfixes

---

### Post by Monstermagnet on 2009-07-19
Hello,

i think it is time to close this thread and start a new one [here]("http://ubuntuforums.org/showthread.php?p=7641480#post7641480").

---

