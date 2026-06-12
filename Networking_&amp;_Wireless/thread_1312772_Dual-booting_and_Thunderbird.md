---
title: "Dual-booting and Thunderbird"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Envergure on 2009-11-03
I'm dual-booting between XP Pro and Karmic.  I only check my email in Windows bacause that way I don't have to look for a message in both OSes.  Is there a way to set up Thunderbird in Linux to use the working directory of the Windows installation?  The goal is to be able to check my email in both Windows and Ubuntu and have all the account settings and messages stored in one directory for both copies of the program.

---

### Post by Envergure on 2009-11-10
I figured it out:

(Note to the reader:  This is a pretty simple, straightforeward process.  Unfortunately, it looks aweful having been described by me!  I think it could use a tough0up from an admin, or better yet someone who can write can make a proper how-to thread.  There is a howto thread about this already, but it's from Dapper Drake (5.10?).  Dapper didn't have reliable NTFS support, so the Thunderbird dual-boot directory-sharing configuration process works out to be pretty darn complicated!)


I'm starting with an existing Thunderbird installation under Windows XP.  If you use Vista or W7, your directories will have different names.

First, you need to find out where Thunderbird on Windows stores the emails.  By default, it's something like:
c:\Documents and Settings\<your Windows username>\Application Data\Thunderbird\Profiles\xxxxxxxxxx.default\Mail\<mail server name>

This is a directory which contains all your messages.  xxxxxxxxxx is a folder where your profile is stored;  <mail server> is something like "pop.gmail.com", it depends on which mail service you use.

Rightl-click your account, and select "Preferences" from the context menu.  Under "Server Settings", you'll find the directory path.  Copy the directory (I have two addresses, therefor two directories) into a text file and save it on your desktop.  Make sure you get the ENTIRE path, it's a bit tricky!

Reboot into Linux.  Mount the partition where Windows is installed (for me, it's called "67GB Filesystem".)  Navigate to your Windows desktop (/media/67GB Filesystem/Documents and Settings/<username>/Desktop) and open the file containing the directories you copied earlier.

Now, you have to install thunderbird.  You can do this in synaptic, but it's faster to run:
```
sudo apt-get install mozilla-thinderbird
```
since I already know the package name.  Once Thunderbird is installed, create your email accounts like you did when you installed Thunderbird in Windows - but DON'T CHECK FOR MESSAGES!  Uncheck that so it doesn't check until later.

Right-click your account, and open the Preferences window.  Under "Server settings", you'll see the "local storage directory" (or whatever it's called).  Click "Browse" and navigate to and open the directory which you copied into the text file from the Windows Thunderbird.  (you can't copy and paste it, unfortunately).

Restart Thunderbird, and all your messages you downloaded in Windows  should be there!

---

