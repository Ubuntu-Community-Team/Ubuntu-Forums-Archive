---
title: "Realplayer File Play"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by frogotronic on 2006-12-05
I was trying to listen to a realplayer stream from the [http://www.democracynow.org/streampage.pl](http://www.democracynow.org/streampage.pl) website.  When Firefox (1.5) asked me which player to use, I choose an incorrect file, and  unfortunately checked the "Always do this action from now on" box.   

How do I reverse this, or reassign the file format to another player?

Thanks,
CH    :confused:

---

### Post by drphilngood on 2006-12-05
Try:
**Edit** -> **Preferences** -> **Downloads** -> **View & Edit Actions**.

edit:
the above was for Iceweasel(what I use) and I think 1.5 but if not, the following is for Firefox 2.0:

**Edit** -> **Preferences** -> **Content** -> **File Types**

I´m getting you close, anyway.:)

---

### Post by frogotronic on 2006-12-06
> **drphilngood said:**
> Try:
**Edit** -> **Preferences** -> **Downloads** -> **View & Edit Actions**.

edit:
the above was for Iceweasel(what I use) and I think 1.5 but if not, the following is for Firefox 2.0:

**Edit** -> **Preferences** -> **Content** -> **File Types**

I´m getting you close, anyway.:)

Nope.  Tried that already.  Unless the file association I want to edit is the SPL type - which I don't think it is.

I've got a work around which is to install MEDIACONNECTIVITY firefox plugin which allows you to choose the media player each and everytime you click on some media files.  It also finds the "terminal" link for the file; which can be very useful.

However, I'd still like to figure out how to reprogramme the file associations for Firefox.

-CH

---

### Post by drphilngood on 2006-12-06
> **cement_head said:**
> Nope.  Tried that already.  Unless the file association I want to edit is the SPL type - which I don't think it is.

I've got a work around which is to install MEDIACONNECTIVITY firefox plugin which allows you to choose the media player each and everytime you click on some media files.  It also finds the "terminal" link for the file; which can be very useful.

However, I'd still like to figure out how to reprogramme the file associations for Firefox.

-CH

> [B]Changing media handling behaviour
From MozillaZine Knowledge Base[/B]


When you download a media file, the MIME type determines what action is taken. Files that are associated with certain plugins like Adobe Acrobat, Quicktime, Windows Media Player and Macromedia Flash will open automatically inside a browser window or in an external player. If no plugin exists, a predefined "helper application" will be used [1] or, if no download action has been defined, you will be prompted to either save the file or open it with a specified application. This article explains how you can change the way downloaded media files are handled.
[edit]
Changing download actions

This will not affect media embedded in a web page - only links to the files themselves. Note that certain file extensions may include multiple entries, one for each MIME type associated with that type of file.

Firefox 1.0.x

Go to "Tools -> Options -> Downloads".

    * To change the helper application or "save to disk" action, select the file type entry you wish to change and click the 'Change Action...' button.
    * To disable the plugin for downloaded files, click the 'Plug-Ins' button and clear the checkmark for the listed entry. The next time you click a download link to that file type, you will get a dialog box prompting you to choose what action to take. 

Firefox 1.5 and later

Firefox 1.5: Go to "Tools -> Options -> Downloads / Download Actions -> View & Edit Actions".

Firefox 2: Go to "Tools -> Options -> Content / File Types -> Manage...".

Select a file type entry and click 'Change Action...'

    * If you want the file to open with the default external program for that file type, select "Open them with the default application"
    * If you want the file to open with an external program other than the default, select "Open them with this application" - you will then be prompted to select an application.
    * If you want the file to be downloaded and saved instead of opened, select "Save them on my computer".
    * If a plugin exists for a file type, you can select "Use this plugin" so that links to files are opened in the plugin. This is the default action when a plugin is available.

[Changing_media_handling_behaviour]("http://kb.mozillazine.org/Changing_media_handling_behaviour")

> [B]Firefox Download Actions
[/B]
The default action for file types for which a plugin is installed is to open the directly-visited file with the plugin. Firefox allows you to change the specified download action for different types of files so that the file is opened with a selected external application or saved to disk instead. If Firefox is not treating files of a certain type in the way you want, view the list of Download Actions (in Tools -> Options under "Downloads" in Firefox 1.5 and earlier, under "Content / File Types" in Firefox 2.0) and change the action as needed. Note that certain file extensions may include multiple entries, one for each MIME type associated with an installed plugin or specified download action. You can see the list of installed browser plugins and related MIME types by entering about:plugins in the address bar. Occasionally, entries may disappear from the list after changing the download action. If closing and reopening the Download Actions window or restarting Firefox doesn't restore the missing entry, try resetting the plugin-related browser preferences as described below. 
[Opening_files_using_plugins]("http://kb.mozillazine.org/Opening_files_using_plugins")

---

