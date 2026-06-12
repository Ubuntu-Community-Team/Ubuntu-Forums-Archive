---
title: "WebDAV unable to open or transfer certain file types"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by Greg_Brown on 2009-11-29
Dear Forum,

I have only recently switched to Ubuntu from Windows XP.  I was an experienced Windows user, but am an extreme novice when it comes to Ubuntu, down to being unaware of what folders programs are stored under and where they store their reg/ini type data.  Please bear that in mind.

I have successfully connected to my company's secure webdav server, and all was going well.  But a problem has arisen.

I cannot download (neither copy & paste nor drag-and-drop) ODT files from my network drive to my local computer.  

Nor can I  directly open ODT files from my network using my local computer. When I try, I get a variety of "not found" or some sort of general I/O error messages.   I **can** download or open other file types such as DOC files, PDF files, and JPG files as expected.  

For example, when I doubleclick a DOC file, it is opened automatically in OO Writer.  But a ODT file is of an "unknown type."  (Local ODT files open fine).  If I direct the computer to use Open Office to attempt the file, I get an error.  If I try to copy the file to my computer, the system reports that the file is "not found."  Interestingly, I can successfully view properties of ODT files, rename them, and delete them--just not open or download them.

(Perhaps related to this problem is the fact that I cannot download folders.  If I attempt to download a folder from webdav to my computer, I get an html file listing the contents of the folder as URLs instead of an actual folder full of actual files.)

This is an extremely curious problem, as it affects only a particular file type.  Unfortunately, I'd already made the switch to Open Office even before switching away from Windows, so many of the the documents I need to access from home are ODT files. 

This seems to be new; I seem to recall opening these files before.  But I've been on Ubuntu only a few weeks.  This occurs on two different machines, one running Jaunty and the other Karmic.

Thank you for any information you can provide!

G

---

### Post by Greg_Brown on 2009-12-01
More information:  

Testing and fiddling around, we've discovered that if the ODT file is merely renamed with a DOC or PDF extension, it can be downloaded and then opened (and opened automatically by OO Writer in the case of DOC; renaming it a PDF file renders it unusable until it is named back to ODT).

Obviously the whole problem lies with the file extension rather than the file itself.  This is an interesting clue, but I don't know where to go with it from here.  Why would a secure WebDAV (accessed from the PLACES>Connect to Server wizard) care what a file's extension is?  Where would such preferences or rules be kept?

In an emergency, changing a file's extension before downloading it is a successful workaround, but it is awkward.  It is ironic that the only file type that seems to not work with Ubuntu's WebDAV (this problem does not occur in Windows) is the default word processor's type.

So, who can provide the solution, or at least a new clue?  

Thanks,

G:?:

---

### Post by Greg_Brown on 2012-05-07
This problem *still* exists today, on a new box with 12.04 installed.

---

### Post by redmk2 on 2012-05-07
> **Greg_Brown said:**
> This problem *still* exists today, on a new box with 12.04 installed.
Interesting (on two levels)...

First, any post that has not been responded to in 1 year is considered dead (necromancy), but in your case you are responding to yourself, so...

As far as your webdav problems, it should be noted that Open Office (and  assume Liber Office) have problems with Nautilus mounted virtual file systems.  You might try ***davfs*** and mount the webdav share via the terminal or using fstab.

See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://savannah.nongnu.org/projects/davfs2") and [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=202761") for some ideas.

---

### Post by Call_M on 2012-08-05
Same problem here. I cannot download matlab m.files. Actually I can not download any file that is marked as an unknown file type on the server. Other files work fine.

I tried it with Nautilus, webbased and Cadaver. Webbased it downloads something but the content of the file is like this:


<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>404 - File or directory not found.</title>
<style type="text/css">
<!--
body{margin:0;font-size:.7em;font-family:Verdana, Arial, Helvetica, sans-serif;background:#EEEEEE;}
fieldset{padding:0 15px 10px 15px;} 
h1{font-size:2.4em;margin:0;color:#FFF;}
h2{font-size:1.7em;margin:0;color:#CC0000;} 
h3{font-size:1.2em;margin:10px 0 0 0;color:#000000;} 
#header{width:96%;margin:0 0 0 0;padding:6px 2% 6px 2%;font-family:"trebuchet MS", Verdana, sans-serif;color:#FFF;
background-color:#555555;}
#content{margin:0 0 0 2%;position:relative;}
.content-container{background:#FFF;width:96%;margin-top:8px;padding:10px;position:relative;}
-->
</style>
</head>
<body>
<div id="header"><h1>Server Error</h1></div>
<div id="content">
 <div class="content-container"><fieldset>
  <h2>404 - File or directory not found.</h2>
  <h3>The resource you are looking for might have been removed, had its name changed, or is temporarily unavailable.</h3>
 </fieldset></div>
</div>
</body>
</html>

---

