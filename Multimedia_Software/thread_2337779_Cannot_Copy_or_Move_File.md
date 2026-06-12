---
title: "Cannot Copy or Move File"
date: 2016-09-21
forum: Multimedia Software
---

### Post by BlacklightHalo on 2016-09-21
I am trying to copy the isomod.ny file with the plugin for audacity into the audacity plugins folder.

I used

```
sudo mv /home/username/downloads/isomod.ny usr/share/audacity/plugins
```

as described [here]("http://askubuntu.com/questions/110138/why-cant-i-paste-anything-under-the-usr-folder#_=_"). The terminal returns, 

> mv: cannot stat ‘/home/username/downloads/isomod.ny’: No such file or directory.

I am writing the file name and directories exactly as they appear in my file browser, but kubuntu cannot seem to tell that either this file or folder in my home directory exist.

---

### Post by howefield on 2016-09-21
Are you using your actual username, also the "*downloads*" folder is probably Downloads.. ie capitalised.

---

### Post by SeijiSensei on 2016-09-21
Also you probably need to use "/usr/share/audacity/plugins" unless you are in the root of the filesystem to begin with.

---

### Post by BlacklightHalo on 2016-09-21
Yes, I am using my actual username. I just replaced it when copying text into the forums, in case it was a security risk. And I also tried capitalising "Downloads," but got the same result.

---

### Post by BlacklightHalo on 2016-09-21
I do not understand your statement. "/usr/share/audacity/plugins" *is* the file path I've been typing into the second half of the "move" command.

---

### Post by howefield on 2016-09-21
> **BlacklightHalo said:**
> I do not understand your statement. "/usr/share/audacity/plugins" *is* the file path I've been typing into the second half of the "move" command.

You didn't have the leading / in the destination path in your original post.

It is usually best to copy/paste the exact terminal input and output in your postings, it will better help others to help you.

What is the output of..

```
ls ~/Downloads
```

---

### Post by BlacklightHalo on 2016-09-21
I see. I apologize for having left that out. Yes, I have tried it exactly as SeijiSensei typed it and gotten the same result.

The output of ls ~/Downloads is very large and contains file names which honestly, I would not think appropriate to post in this forum. But clearly the machine recognizes the existence of the directory and also the file in question. It just returns that one or both don't exist when I run the command in the terminal.

---

### Post by BlacklightHalo on 2016-09-21
*Update - I seem to have found the problem. I did not capitalize the file name itself. That's why it wasn't recognized. I will mark this thread as solved. Thank you for your help.

---

### Post by howefield on 2016-09-22
> **BlacklightHalo said:**
> The output of ls ~/Downloads is very large and contains file names which honestly, I would not think appropriate to post in this forum. But clearly the machine recognizes the existence of the directory and also the file in question.

Cool, was only to confirm existence and actual name of the file in question.

> **BlacklightHalo said:**
> *Update - I seem to have found the problem. I did not capitalize the file name itself. That's why it wasn't recognized. I will mark this thread as solved. Thank you for your help.

Well done on sussing it out. You might be interested in "tab completion" to aid getting the names and paths right eg.. typing ~/Dow then hitting the tab key will complete to ~/Downloads - continue typing ~/Downloads/Iso and the tab key will complete to ~/Downloads/Isomod.ny and so on.

In your case, when you typed the lower case ~/Downloads/iso it won't autocomplete so you know something is up, either there is more than one file starting with those letters (in which case pressing the tab key again will show you the alternatives) or the file doesn't exist under that name (linux being case sensitive). Once used to using the tab key you can save both time and error.

---

