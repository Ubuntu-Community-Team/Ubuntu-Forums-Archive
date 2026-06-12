---
title: "Veoh Player working with Wine on Feisty"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by carlotheman on 2007-08-06
As we know, Veoh Networks is a great place to trade productivity for entertainment, but usually, we as Linux users, feel a bit left out after five minutes at the most.

Luckily, I found that the Veoh Player actually CAN work on Ubuntu, with the help of the infinitely compatible Wine. But to call that trivial would be a little on the light-hearted side, and entertainment is a serious business. So, I decided, it is time for a little guide.

** Note: This will probably work in principle on other incarnations of GNU/Linux too, but it took a little experimenting to find the right version of Veoh Player to do the job right; so if you're using something else than Ubuntu 7.04 Feisty Fawn this could very well be true for you too. Please feel encouraged to tinker yourself... and maybe write a guide!

In order to never think about what to do next again (if you don't mind sitting in front of a screen all day), you need:

* Ubuntu Feisty Fawn & Wine [Please install this via Synaptic, apt-get, ...]
* Mozilla Firefox for Windows, Version 2.0.6 (Yes, for *Windows*) [[Download]("http://www.mozilla.com/en-US/products/download.html?product=firefox-2.0.0.6&os=win&lang=en-US")] 
* Veoh Player for Windows, Version 3.2.1.1073 [[Download]("http://ll-appserver.veoh.com/downloads/VeohSetup-3.2.1.1073.exe")]
* A Veoh.com account [[Create]("http://www.veoh.com/login.html?redir=1&noAction=1")]
* Approximately 50MB disk space (plus several GB for videos)

I started out by installing FireFox for Windows. After downloading, I simply doubleclicked the downloaded file. A typical Windows installer box showed up, which I endured to the end, when it asked me to launch Firefox, which I did. I agreed to let FireFox be my default browser and closed.

Firefox is necessary because the VeohClient only downloads files, but you need some way of knowing which file you want it to download; this, it does through a browser plugin which gets activated when you click the 'Download' link of a video on Veoh.com. So the easiest way I know of to get that browser plugin activated is to install FireFox for Windows first.

Next I installed Veoh for Windows. Installation was rather straight-forward, with the same installation routine that luckily we mostly don't have to spend countless hours of hour lives with using Ubuntu, most of the time. (I am happy we can spend countless hours of hour life watching Internet video instead.) I used all default options here.

After doing this (and waiting unreasonably long at the 'Publishing Product Information' step), Veoh Client started up, just like it would in Windows. Wine prompted me to install 'Gecko for Wine', to which I agreed. After a convenient installation procedure, Veoh was there. I quickly closed the 'introduction' page before it could cause me any trouble.

I right-clicked the tray Icon and selected 'Settings' from the menu. There, I de-activated Pop-Up messages in the 'Download' tab (they're slow when running Veoh this way) and pressed the 'Enter' key (some buttons don't show up properly but they do work, and pressing enter is easier than clicking in the dark with a mouse).

I was ready. So I logged into my account on Veoh from the Windows Firefox, and selected a video I wanted to watch (I'm too embarrassed to tell you which one it was). I clicked the download link, and Presto! Download started.

It was a defining moment of my life. May it be for you.

Carlo

---

### Post by aeto on 2007-09-24
I wonder why this hasn't received a bump. Definitely a good method.

---

### Post by Smashing Pumpkin on 2007-10-23
Thanks - just followed these instructions in Gutsy and it worked :)

---

### Post by avgeneral on 2007-12-10
Does it work in Gutsy?

---

### Post by prasincs on 2007-12-13
Yes, it does, just remember to put XP emulation mode in winecfg :) My wine had some issues with that because I was emulating win98 for some games.:KS

---

### Post by sjc1963 on 2007-12-15
Double Post.

---

### Post by sjc1963 on 2007-12-15
I had no trouble installing the Windows version of Firefox 2.0.0.11, but when I go to install the Veoh Player I get an error "1628: Failed to complete installation."

I'm using Gutsy and version 0.9.51 of WINE.

---

### Post by uberjay on 2007-12-18
> **sjc1963 said:**
> I had no trouble installing the Windows version of Firefox 2.0.0.11, but when I go to install the Veoh Player I get an error "1628: Failed to complete installation."

I'm using Gutsy and version 0.9.51 of WINE.

I have the exact same problem. Any ideas?

---

### Post by KrotBot on 2007-12-27
just found this post and am having the same 1628 error. Any clue why?

---

### Post by v_krishna on 2008-01-20
same problem here, too. tried it with numerous versions of veohtv, always the same problem...

anybody found a fix and/or figured out more about why this might not work anymore?

---

### Post by scubasteve657 on 2008-02-03
Same Problem.  Here's what wine's complaints are:
"Call from 0x6d6679df to unimplemented function KERNEL32.dll.BaseIsAppcompantInfrastructureDisabled, aborting"

---

### Post by p4cldba on 2008-02-03
I am also finding problem to configure veoh on Gutsy. will appreciate any help.

thanks in advance
-P

---

### Post by Noaptus on 2008-02-13
ok. ok

i installd the veoh player and that is fine. 


I was ready to go, So I logged into my account on Veoh from the Windows Firefox and selected a video I wanted to watch I clicked the download link, and i haf this error 

Sorry! This video is outside your content filter setting.??????

pls help.....

Iceland

Yes all the pluginns ar there.... fore the Firefox

Ubuntu 7.10 Gusty

---

### Post by valke on 2008-02-16
> I was ready to go, So I logged into my account on Veoh from the Windows Firefox and selected a video I wanted to watch I clicked the download link, and i haf this error

Sorry! This video is outside your content filter setting.??????

hah. from your browser, log into veoh and turn off the family filter. it's no biggie :]

after you log in, go here: [https://www.veoh.com/mySettings.html](https://www.veoh.com/mySettings.html)

i don't really remember, but i think it will ask you to verify your age possibly.

then restart veoh tv.

cheers!

---

### Post by fade_out on 2008-02-25
I tried this on Gutsy, firefox install and veoh install went ok, but when wine tries to launch veoh, after it installs the gecko engine a dialog box appears saying 
"There was an error loading Internet Explorer. Please make sure Internet Explorer is installed and working correctly."

I click ok and the veoh welcome page comes up asking me to input my user/pass, but the text fields do not accept the cursor and when i mouseover any link on that page the page and veoh crashes.

Any help is appreciated.

---

### Post by sloggerkhan on 2008-02-25
stage6 is better than veoh, IMO. Didn't veoh start making it so all their stuff was downscaled and re-encoded?

---

### Post by fade_out on 2008-02-25
Just reading OP I realised I didn't use the veoh installer specified (I used the latest one from Veoh site) Using the original everything works now. :redface: 
They need to realease a native version though, which I've read they have. 
Slogger- ya I think they started encoding nearly everything to lower quality flash and it sucks compared to original uploads, stage6 is much better.

---

### Post by _Stevie_ on 2008-02-27
stage6 was better... 
the service has ceased.

---

### Post by alexjohnc3 on 2008-03-03
> **fade_out said:**
> I tried this on Gutsy, firefox install and veoh install went ok, but when wine tries to launch veoh, after it installs the gecko engine a dialog box appears saying 
"There was an error loading Internet Explorer. Please make sure Internet Explorer is installed and working correctly."

I click ok and the veoh welcome page comes up asking me to input my user/pass, but the text fields do not accept the cursor and when i mouseover any link on that page the page and veoh crashes.

Any help is appreciated.
I'm having the same problem, except I can only see the error message with black around it.

Edit: Never mind. I read fade_out's second post. The same solution (using the download specified by the OP) works. It doesn't work very well though and I keep seeing black stuff the windows.

Edit 2: While I was able to install it, I wasn't able to download anything.

---

### Post by coreyinprogress on 2008-03-03
> **alexjohnc3 said:**
> I'm having the same problem, except I can only see the error message with black around it.

Edit: Never mind. I read fade_out's second post. The same solution (using the download specified by the OP) works. It doesn't work very well though and I keep seeing black stuff the windows.

Edit 2: While I was able to install it, I wasn't able to download anything.


Make sure you are using the Windows FIrefox through Wine when trying to Download.  I have blackness around the windows as well - so I'd say just use hotkeys!  I just got the entire thing going, and its working fine.  Very easy if you use the links provided.

Still - I think we can agree, VEOH is a far cry from Stage6

---

### Post by l.h.lion on 2008-03-06
After following the installation procedure, and select a video to download, I can see it in the Veoh download directory, but with size 0. Veoh  client has decided to download the last version  VeohSetup-3.8.1.1011.exe and the download of the video seems to be stopped. Any suggestions (apart from being patient)?

In fact the download of the video has stopped and veoh client shows unknown error. Let me just give a few more information on how I download the video.

From the veoh site, I click on Download Options and then select Download video (on this computer)

I would appreciate very much your help.

--------

Well it turned out that patience worked; other videos are downloaded. Nevertheless, I find the client a bit fragile, canceling one video download closes the Veoh window, and after that right-click settings do not work, and I am not sure how this affects the other downloads.

Nevertheless, it is a great solution, thanks.

---

### Post by slimjimflim on 2008-03-08
i tried the latest and the older version.  the old one actually installed, but when i clicked 'open in veoh tv' the site made me upgrade.  the latest version crashes when you mouse over the main window.  i also got the ie not installed error even though it is.  this is me hitting a brick wall.  

p.s. veoh, if you're listening, make it native !?!?!?!?!

---

### Post by daMask on 2008-03-16
I am having the same problem as slimjimflim...
I got everything installed, but when I try to download a video, it forces an upgrade, but the upgrade doesn't complete.

---

### Post by baroi on 2008-03-25
where do we buy the video veoh for ubuntu?

---

### Post by baroi on 2008-03-26
I think the Ubuntu is the best OS.... but, we need to re-do the installation format....

for the installation of third party, we need the UBUNTU OS will accept all of the SETUP / INSTALL format including an extension  .EXE    or    .BAT    or   .COM   likes windows does. So we have no problem to install or setup all of the third parties software.....

Don't you think?

---

### Post by muchas on 2008-03-26
> **baroi said:**
> I think the Ubuntu is the best OS.... but, we need to re-do the installation format....

for the installation of third party, we need the UBUNTU OS will accept all of the SETUP / INSTALL format including an extension  .EXE    or    .BAT    or   .COM   likes windows does. So we have no problem to install or setup all of the third parties software.....

Don't you think?

if so Linux distros like Ubuntu will not be virus free anymore

---

### Post by petit_prince on 2008-04-07
Regarding your initial attempt to watch Veoh videos on Ubuntu, there's a tool which supports the new protocol they appear to use, check out my post at
[http://ubuntuforums.org/showpost.php?p=4669727&postcount=9]("http://ubuntuforums.org/showpost.php?p=4669727&postcount=9")

---

### Post by logari81 on 2008-05-05
In reality it is much easier to use veho under Linux/Ubuntu than in other OS's.

You don't even need to install any programs. Just use the attached skript I've found on net.

Its usage:

for example for the following video
[http://www.veoh.com/videos/v6811251bKHJ5FxT](http://www.veoh.com/videos/v6811251bKHJ5FxT)

you have to run
$ ./getveoh v6811251bKHJ5FxT

---

### Post by sirwitti on 2008-05-06
this script has the same problem as several other "solutions" as you can see only the first 5 minutes of a video (=the preview).
any other possible ways of watching full veoh vids on ubuntu/linux?
thx, witti

---

### Post by petit_prince on 2008-05-06
> **sirwitti said:**
> this script has the same problem as several other "solutions" as you can see only the first 5 minutes of a video (=the preview).
any other possible ways of watching full veoh vids on ubuntu/linux?
thx, witti

sirwitti, please have a look at the posts #9 and #10 of this thread:
[http://ubuntuforums.org/showthread.php?t=666226]("http://ubuntuforums.org/showthread.php?t=666226"). Veoh recently performed some changes to their systems which rendered former solutions useless, but the ones provided in that thread work for me; e.g. the VeohDownload program from [http://www.assembla.com/spaces/files/bwEUBC9pCr3indabIlDkbG]("http://www.assembla.com/spaces/files/bwEUBC9pCr3indabIlDkbG")

---

### Post by _Stevie_ on 2008-05-10
thats w wine solution, nothing linux native, right?
or did i miss something?

---

### Post by BwackNinja on 2008-05-12
Good news for anyone who is actually reading this thread :D VeohTV BETA (yes, the newest version) does in fact work in wine, and pretty well (I was able to easily watch a video in it) but with a couple quirks...

-Installer crashed for me...I just took the extracted msi from the exe found in /home/mike/.YOUR_WINEPREFIX/drive_c/windows/Downloaded Installations/{RANDOM LETTERS, NUMBERS, AND DASHES GO HERE}/veoh.msi when the installer crashes and extracted with windows "msiexec /a veoh.msi /qb TARGETDIR=C:\veoh-temp\" run in a batch file in the directory of the msi.

-Channels causes it to crash...yea kinda sucks but not the main deal anyway

-UI? Works but only after some dll overrides (I installed IE6, the manual way as shown on appdb.winehq)

-login? yea...this was the hardest part, I got it to stop crashing at start by looking at the output, and added 2 dlls - pdh.dll and odbcbcp.dll which I downloaded and set to (native, builtin) in winecfg buuuut, since the method it uses to login doesn't work, I installed in windows, logged in there, exported the registry keys and imported them to my wine with "wine regedit" worked like a charm

If anyone wants a full howto, I'll make a new thread for one (aka at least someone responds and thinks this is nice)

Also, screenshot of it in action is attatched, just for proof :P

---

### Post by El Lance-O on 2008-05-17
> **BwackNinja said:**
> Good news for anyone who is actually reading this thread :D VeohTV BETA (yes, the newest version) does in fact work in wine, and pretty well (I was able to easily watch a video in it) but with a couple quirks...

-Installer crashed for me...I just took the extracted msi from the exe found in /home/mike/.YOUR_WINEPREFIX/drive_c/windows/Downloaded Installations/{RANDOM LETTERS, NUMBERS, AND DASHES GO HERE}/veoh.msi when the installer crashes and extracted with windows "msiexec /a veoh.msi /qb TARGETDIR=C:\veoh-temp\" run in a batch file in the directory of the msi.

-Channels causes it to crash...yea kinda sucks but not the main deal anyway

-UI? Works but only after some dll overrides (I installed IE6, the manual way as shown on appdb.winehq)

-login? yea...this was the hardest part, I got it to stop crashing at start by looking at the output, and added 2 dlls - pdh.dll and odbcbcp.dll which I downloaded and set to (native, builtin) in winecfg buuuut, since the method it uses to login doesn't work, I installed in windows, logged in there, exported the registry keys and imported them to my wine with "wine regedit" worked like a charm

If anyone wants a full howto, I'll make a new thread for one (aka at least someone responds and thinks this is nice)

Also, screenshot of it in action is attatched, just for proof :P

YES!

I successfully installed the beta version, but it gives me a bug report on start up, and the GUI is very glitchy.

I've tried everything to get it to work, but it just doesn't want to download or stream anything.

A how-to would be VERY awesome. I'll be sure to check up so I know as soon as it's available.

Thank you!

---

### Post by BwackNinja on 2008-05-17
HOWTO complete, and works better than my last post (AFAIK it works flawlessly)
[http://ubuntuforums.org/showthread.php?p=4982283](http://ubuntuforums.org/showthread.php?p=4982283)

---

### Post by logari81 on 2008-05-18
It is not long time ago that I downloaded videos longer than 5 min using the skript posted in #28 but unfortunately it seems no longer to work after the changes in the site of veoh. Veoh sucks.

---

### Post by Fazz Munkle on 2008-05-20
Installs fine but I get a bug report window when I launch Veoh. I'm assuming it crashed. But the notification icon persists.

I'm using Ubuntu 8.04 and CrossOver Games (a WINE branch). I installed into a WinXP bottle, but no go.

---

### Post by logari81 on 2008-05-31
unbehagen posted a non-wine solution in the following thread:

[http://ubuntuforums.org/showthread.php?t=666226&page=2](http://ubuntuforums.org/showthread.php?t=666226&page=2)

it is a python skript which downloads the original video and worked fine for me when I tried it.

For people that don't like wine and non-native non-opensource programs its a very nice solution.

---

### Post by jorgethe.bulldog on 2008-07-15
> **sloggerkhan said:**
> stage6 is better than veoh, IMO. Didn't veoh start making it so all their stuff was downscaled and re-encoded?

 stage 6 is shut down!

---

### Post by apche93 on 2008-07-16
hi everyone,


I tried the steps mentioned by the thread starter, and i ended up with the following:
[IMG]http://i260.photobucket.com/albums/ii30/apche93/Screenshot-1-1.png[/IMG]

After 2 seconds, that window closed and a bug report shows up:
[IMG]http://i260.photobucket.com/albums/ii30/apche93/Screenshot-2.png[/IMG]

After trying to run VeohClient.exe in terminal, i get:
```
$ wine VeohClient.exe
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
wine: Call from 0x7b844b20 to unimplemented function pdh.dll.PdhEnumObjectItemsW, aborting
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:ole:CoResumeClassObjects stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:shdocvw:InternetExplorer_ShowBrowserBar (0x12de58)->(0x143390 0x1433b0 0x1433d0)
fixme:shdocvw:InternetExplorer_Quit (0x12de58)
apoorv@apoorv-laptop:~/.wine/drive_c/Program_Files/Veoh_Networks/Veoh$ fixme:shdocvw:InternetExplorer_ShowBrowserBar (0x12de18)->(0x14a9a8 0x14a9c8 0x14a9e8)
fixme:shdocvw:InternetExplorer_Quit (0x12de18)
fixme:shdocvw:InternetExplorer_ShowBrowserBar (0x12d8b8)->(0x14af50 0x14af70 0x14af90)
fixme:shdocvw:InternetExplorer_Quit (0x12d8b8)

```

Does anyone know the reason for this??

Plus, whats the point of installing the windows version of firefox?


Add'l info:
The installer ran fine and finished successfully.  But when i tried to launch Veoh the above conditions came!

Anyone have fix for this?

---

