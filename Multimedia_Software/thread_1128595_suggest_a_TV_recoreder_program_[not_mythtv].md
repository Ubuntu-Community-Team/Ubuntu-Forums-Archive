---
title: "suggest a TV recoreder program [not mythtv]"
date: 2009-04-17
forum: Multimedia Software
---

### Post by ant2ne on 2009-04-17
My TV tuner works fine. I can watch TV with TVtime just fine.

I've been discouraged with the complexity and setup/installation problems of mythtv. I'm looking for a TV recording program that "just works". Something apt-get'able would be great. What I want is something that will simply let me set a time and date and channel and it will just record what I want in avi/mpg format and leave it for me to watch later. It isn't even really important to me to be able to set multiple schedules.

Anything out there that you know of that fits my needs?

---

### Post by Bloemetjesgordijn on 2009-04-17
how about MeTv [https://launchpad.net/me-tv](https://launchpad.net/me-tv)

---

### Post by lovinglinux on 2009-04-17
You could try my extension for Firefox, called [FoxMediaCenter](http://fmc.isgreat.org/). Is a lightweight media center with TV recording, EPG, Playlits Manager and more. Is not complicated to setup and can do what you want

With FoxMediaCenter you are able to:

    * import xmltv programme schedules or add them manually
    * schedule TV recordings
    * start TV recordings on-the-fly and use time-shifting
    * record weekly TV series automatically based on show status
    * setup reminders of your favorite programme
    * keep track of TV series status and airing day
    * keep track of watched programme
    * create media playlists (videos, music and tv recordings) using tags or keywords
    * browse and view your favorite media folders
    * search IMDB, TV.com, TV Guide and media (trailer, posters and wallpapers)
    * launch TvTime from Firefox
    * and more

Here are some screenshots of the recorder tool:

[[IMG]http://img7.imageshack.us/img7/2456/screenshotfoxmediacente.th.png[/IMG]](http://img7.imageshack.us/img7/2456/screenshotfoxmediacente.png) [[IMG]http://img7.imageshack.us/img7/9766/screenshotfoxmediacentec.th.png[/IMG]](http://img7.imageshack.us/img7/9766/screenshotfoxmediacentec.png)

---

### Post by MeKino on 2009-04-18
I use vlc which I record via crontab script. Here's a link to a thread with some details:

[http://ubuntuforums.org/showthread.php?t=758845](http://ubuntuforums.org/showthread.php?t=758845)

---

### Post by ant2ne on 2009-04-18
MeTV looked promising, but had no install option for Hardy. I'm happy with LTS and don't want to upgrade. I don't know if using MeTV on hardy will cause problems, so I'm not going to attempt it at this time.

VLC and the scripts looked intriguing. I like scripts and have a lot of fun with them, But I would like something point and click so when I get home (from my IT job) I don't have to think or type while setting it up.

The Fire Fox Media Center is both interesting and just might fit my needs. It looks like it might be some reading [http://fmc.isgreat.org/](http://fmc.isgreat.org/) to set it up properly. So could you give me some incentive and drop me a hint on how to configure it to record a certain channel at a certain time and save it as avi?

---

### Post by lovinglinux on 2009-04-18
> **ant2ne said:**
> The Fire Fox Media Center is both interesting and just might fit my needs. It looks like it might be some reading [http://fmc.isgreat.org/](http://fmc.isgreat.org/) to set it up properly. So could you give me some incentive and drop me a hint on how to configure it to record a certain channel at a certain time and save it as avi?

The recording tool is pretty easy to use. I recommend that you at least read the instructions on these pages:

[http://fmc.isgreat.org/index.php?option=com_content&view=article&id=10&Itemid=11&lang=en](http://fmc.isgreat.org/index.php?option=com_content&view=article&id=10&Itemid=11&lang=en)
[http://fmc.isgreat.org/index.php?option=com_content&view=article&id=21&Itemid=23&lang=en](http://fmc.isgreat.org/index.php?option=com_content&view=article&id=21&Itemid=23&lang=en)
[http://fmc.isgreat.org/index.php?option=com_content&view=article&id=35&Itemid=39&lang=en](http://fmc.isgreat.org/index.php?option=com_content&view=article&id=35&Itemid=39&lang=en)
[http://fmc.isgreat.org/index.php?option=com_content&view=article&id=13&Itemid=14&lang=en](http://fmc.isgreat.org/index.php?option=com_content&view=article&id=13&Itemid=14&lang=en)

Then when you have time you can read the rest, since they are related to the EPG functions and other features of the extension.

---

### Post by ant2ne on 2009-04-18
I can't seem to figure out how to get anything in the EPG tabs.  ;-(

---

### Post by lovinglinux on 2009-04-19
> **ant2ne said:**
> I can't seem to figure out how to get anything in the EPG tabs.  ;-(

You need to [add TV schedules manually](http://fmc.isgreat.org/index.php?option=com_content&view=article&id=14&Itemid=15&lang=en) or [import them from a xmltv file](http://fmc.isgreat.org/index.php?option=com_content&view=article&id=30&Itemid=31&lang=en), then reload the extension to see the schedules in the tabs.

---

### Post by ant2ne on 2009-04-19
> XMLTV File Path:  this is the same option available in the extension preferences and should be the full path to your xmltv file.

Download and Save:  when you first hit the "Download and Save" button you wil be prompted to edit the download script. This is useful if you already have a script to grab or download xmltv sources. Replace the code with your script code, then hit the "Download and Save" button again. Please notice that when you do this, the file specified in the "XMLTV File Path" will be overwritten. If you don't have a download script and you get the xmltv file using other tools, then simply fill the form with the path to the xmltv file on your hard drive. I connect to FoxMediaCenter, choose XMLTV and I get the pop up box "XMLTV", I click the settings tab and "Download and Save" and a new pop up box titled "Information" which goes on to say 
> To use this feature you need to edit the download script! Once you close this window, the file will be opened for you with the text editor chosen in the preferences.I click OK and I get the script in the text editor, just like it said. But there are no hints as to what the script should say or how to make it work. It just says the following 
```
#!/bin/bash

#placeholder-release-ok

#REPLACE THIS CODE WITH YOUR XMLTV DOWNLOAD SCRIPT
zenity --info --text "To use this feature you need to edit the download script! Once you close this window, the file will be opened for you with the text editor chosen in the preferences." &&

${2} ${0}
```Closing this script doesn't do anything. The file ~/Desktop/xmltv.xml is never generated, and importing then fails. What should this script say and do?

I don't see any valuable information on this linky [http://fmc.isgreat.org/index.php?option=com_content&view=article&id=14&Itemid=15&lang=en]("http://fmc.isgreat.org/index.php?option=com_content&view=article&id=14&Itemid=15&lang=en")

This seems to be the opposite of "just works"  :???:

---

### Post by lovinglinux on 2009-04-19
> **ant2ne said:**
> I connect to FoxMediaCenter, choose XMLTV and I get the pop up box "XMLTV", I click the settings tab and "Download and Save" and a new pop up box titled "Information" which goes on to say 
I click OK and I get the script in the text editor, just like it said. But there are no hints as to what the script should say or how to make it work. It just says the following 
```
#!/bin/bash

#placeholder-release-ok

#REPLACE THIS CODE WITH YOUR XMLTV DOWNLOAD SCRIPT
zenity --info --text "To use this feature you need to edit the download script! Once you close this window, the file will be opened for you with the text editor chosen in the preferences." &&

${2} ${0}
```Closing this script doesn't do anything. The file ~/Desktop/xmltv.xml is never generated, and importing then fails. What should this script say and do?

The "Download and Save" is for people who already have a xmltv download script and want to incorporate it on the extension. Is an advanced and optional feature. Please read the text in red on the quote below.

> Download and Save:  when you first hit the "Download and Save" button you wil be prompted to edit the download script. **[color=#FF0000]This is useful if you already have a script to grab or download xmltv sources.[/color]** Replace the code with your script code, then hit the "Download and Save" button again. Please notice that when you do this, the file specified in the "XMLTV File Path" will be overwritten.** [color=#FF0000]If you don't have a download script and you get the xmltv file using other tools, then simply fill the form with the path to the xmltv file on your hard drive.[/color]**

Downloading a xmltv is a service that some sites provide so you don't have to generate the file yourself. This is very specific for each country/area and I can't provide scripts for everyone. For example, I provide [instructions here](http://fmc.isgreat.org/index.php?option=com_content&view=article&id=36&Itemid=41&lang=en) on how to edit the script for users in Brazil, since there is a site where you can download a xmltv file with all TV schedules from all TV stations in the country.

If you have a xmltv file provider in your country, but don't have a download script, then you still can use the extension xmltv features by simply downloading the file manually and filling the path to the xmltv file on your hard drive as already stated in the quoted instructions.

So basically the "Download and Save" script is a tool for automating the download of the xmltv file from a known source. But if you don't have a source to download from, then this feature won't create a xmltv file for you.

If you don't have a valid xmltv file than you have to create one by using a xmltv grabber like [xmltv-druid](http://gshowtv.sourceforge.net/xmltv-druid.html).

To learn more about xmltv read this:

# [XMLTV home page](http://www.xmltv.org/)
# [XMLTV project page at SourceForge.net](http://sourceforge.net/projects/xmltv)
# [XMLTV related projects (viewers, grabbers)](http://xmltv.org/wiki/xmltvrelatedprojects.html)
# [Television Listings and XMLTV article at xml.com](http://www.xml.com/pub/a/2004/02/18/xmltv.html)

> **ant2ne said:**
> I don't see any valuable information on this linky [http://fmc.isgreat.org/index.php?option=com_content&view=article&id=14&Itemid=15&lang=en]("http://fmc.isgreat.org/index.php?option=com_content&view=article&id=14&Itemid=15&lang=en")

What do you expect? You just have to fill the forms with the info of a TV programme schedule and hit the submit button. As already stated there, this is useful if you don't have a xmltv file to import, so you can add programme manually. Most EPG softwares does not allow you to do this, so you need a xmltv to use them. My extension provides an alternative method if you feel that working with xmltv file is too complex or if you don't have a way to generate one.

The information on that link explains the difference between each tab and also what it is each field in the forms. What else do you need?

> **ant2ne said:**
> This seems to be the opposite of "just works"  :???:

I don't like your attitude. You wanted to cut corners since the beginning, because the site had instructions to read. Now you come here again criticizing the extension, the tutorials and putting words on my statements about something you didn't asked in the first place. You asked for a simple recorder and that's what I  delivered to you. 

I never claimed that the EPG or the XMLTV feature "just works". The configuration can be complicated if you don't know the concept of xmltv. Nevertheless, it's much more simple than MythTV and you don't have to use the EPG or the XMLTV features of my extension to record TV. If you want, then at least you must be familiar with xmltv or add programme schedules manually, as already explained.

I came here to share the extension with you, because I thought you might find it useful. As many people on this community, I don't get any money from it or from supporting users on this forum and I'm doing my best to help you out. Additionally, I tried to make the site instructions as easy as possible to understand. I could provide more information on the site, but I think that is the necessary info to make it work. Besides, additional questions can be solved on a user basis in the forum.

So if you don't want to read the instructions properly, get familiarized with the extension functions and ask question without baseless criticism, then I suggest you use only the recorder or find another tool that suit your needs.

---

### Post by ant2ne on 2009-04-19
> You asked for a simple recorder and that's what I delivered to you.

I have ready this page several times. While it does do a adequate job of explaining 'what' everything is on the page, it does a poor job of describing 'how' do get it to work.


> 'This seems to be the opposite of "just works"' I don't like your attitude. You wanted to cut corners since the beginning,  wasn't that what I said? something simple without a lot of hassle and "just works" 
>  Now you come here again criticizing the extension, the tutorials  tutorial? Where? I'd like that please. My only criticism was that it didn't "just work". In fact, I think you are on to an awesome application / add on and could really fill a valuable niche. I do like the approach and the concept. (And I say you because you seem to be the only one promoting this application /add on.) I just want something dumbed down a little.
>  and putting words on my statements about something you didn't asked in the first place. You asked for a simple recorder and that's what I delivered to you.If, what you delivered to me was a simple program, then I'd have it working. Maybe, what I need is something with less features, and just more end user support and direction. A nice hyper on the website with a "how to" section might be wonderful.

Like I said, I spend all day at work trying to make software work. (Dang Microsoft Windows Computers) I don't want to have to 'work' at this.

---

### Post by lovinglinux on 2009-04-19
> **ant2ne said:**
> I have ready this page several times. While it does do a adequate job of explaining 'what' everything is on the page, it does a poor job of describing 'how' do get it to work.


 wasn't that what I said? something simple without a lot of hassle and "just works" 
 tutorial? Where? I'd like that please. My only criticism was that it didn't "just work". In fact, I think you are on to an awesome application / add on and could really fill a valuable niche. I do like the approach and the concept. (And I say you because you seem to be the only one promoting this application /add on.) I just want something dumbed down a little.
If, what you delivered to me was a simple program, then I'd have it working. Maybe, what I need is something with less features, and just more end user support and direction. A nice hyper on the website with a "how to" section might be wonderful.

Like I said, I spend all day at work trying to make software work. (Dang Microsoft Windows Computers) I don't want to have to 'work' at this.

Sorry. Maybe I overreacted to your comments because the extensions has been downloaded almost 1000 times and nobody complained before. Besides, this is my first extension so maybe I'm overzealous.

I'm not considering creating a step-by-step tutorial for all features because most of the required user interaction is form based, which means the user just have to fill a form and submit it to take effect. I don't believe I have to describe every step of how-to fill a form and click the submit button over and over, if I have already explained what each field means and how they interact with the extension. Nevertheless, the "User Guide" in the site is formatted in a way that if you follow each section in order, you shouldn't have any issues.

If there is anything else I can help you with or if there is any question I didn't answer, please feel free too continue asking. English is not my first language, but I will try to make self clear enough so you can understand.

Did you understand that you need a valid xmltv file to use it with the extension, otherwise you will have to add programme schedules manually?

Just to remind you, you don't have to use xmltv or the EPG to record TV, since the recorder has a tool for selecting the channel, duration and time of the recording, which is independently from the EPG programming schedule.

---

