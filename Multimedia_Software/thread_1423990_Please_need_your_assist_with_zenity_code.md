---
title: "Please need your assist with zenity code"
date: 2010-03-07
forum: Multimedia Software
---

### Post by seanbw on 2010-03-07
I am trying to make the iplayergui.sh download straight into my videos directory without asking asking me for a name since I always save into the videos directory which is at /home/seanbw/Videos/

I have tried ```
Directory=$(zenity --file-selection --directory --filename=/home/seanbw/Videos/ --title "$WindowTitle" --width 500);
``` but all it does is create layers of directories in Videos. I tried to remove --directory and it goes to the videos directory and then goes thbrough the motions and closes but t does not record anything so I know I am breakng the code somewhere.
Can anyone point me in the direction of how I can alter the code such that it takes the url from me and saves directly to the videos directory in a directory previously set up called BBC?
Please! 
I have tried but I can't get it to save without creating multiple layers of directories.
The full code is this:
```
#!/bin/bash
#---------------------------------------------------------------
# Description: GTK GUI for Paul Battley's iplayer-dl script
# Author: Matt Clarke, TechPad.co.uk
# Dependencies: zenity, iplayer-dl, ruby
#---------------------------------------------------------------

# Phrases
  WindowTitle="iPlayer Downloader"
  MessageEnterUrl="Enter iPlayer URL"
  MessageTypePreference="Do you want the normal version or the subtitled version?"
  MessageDownloading="Downloading programme now..."
  MessageDone="Your iPlayer download has completed!"
  MessageNotInstalled="iplayer-dl was not found.\n\nPlease install and configure iplayer-dl to continue."
  ColumnDownload="Download"
  ColumnVersion="Version"

# Check to see if iplayer-dl is installed as it's a pre-requisite
if [ $(basename `which iplayer-dl`) !="iplayer-dl" ]; 
    then zenity --title "$WindowTitle" --error --text "$MessageNotInstalled"
    exit
fi

# Ask user for iPlayer URL
iPlayerURL=$(zenity --entry --text "$MessageEnterUrl" --title "$WindowTitle" --width 500);
if [ $? = 1 ];
then exit
fi

# Ask the user to select a download directory

Directory=$(zenity --file-selection --directory --title "$WindowTitle" --width 500);
if [ $? = 1 ];
then exit
fi

# Ask the user whether they want the original version or signed version
TypePreference=$(zenity --title "$WindowTitle" --text "$MessageTypePreference" --list --radiolist --width 500 --column "Select" --column "Version" True original False signed);
if [ $? = 1 ];
then exit
fi

# Download using iplayer-dl and pipe output to zenity for progress bar
iplayer-dl $iPlayerURL -d $Directory -s --type-preference=$TypePreference 2>&1 | zenity --progress --title "$WindowTitle" --text="$MessageDownloading" --width 500 --auto-kill --auto-close
if [ $? = 1 ];
then exit
fi

# Show download success message
zenity --info --title "$WindowTitle" --text "$MessageDone"
exit
```
:confused:
Many thanks. coding is a gift and I just dont have it. If you can help,I am grateful. Cheers

---

### Post by matchett808 on 2010-03-07
not tried it but after a 2 minute look have you tried replacing:

Directory=$(zenity --file-selection --directory --title "$WindowTitle" --width 500);
if [ $? = 1 ];
then exit
fi


with:


Directory="/home/videos/"


Worth a try?

it just fills the variable for you....no dialog box...

---

### Post by matchett808 on 2010-03-07
after a bit more debugging I cannot see why it would be giving you a bad exit code (or at least not 0 lol) also (to debug some more) add in echo $? after the "Directory=......" line but BEFORE you if loop....

---

### Post by matchett808 on 2010-03-10
Is the **OP** still around?

---

