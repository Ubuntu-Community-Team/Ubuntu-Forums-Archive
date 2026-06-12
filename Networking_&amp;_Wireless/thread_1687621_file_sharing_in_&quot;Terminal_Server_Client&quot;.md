---
title: "file sharing in &quot;Terminal Server Client&quot;"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by karpay on 2011-02-14
Hi,

I'm using ubuntu 10.10 and I'm establishing a remote desktop application to Windows 7 using the "Terminal Server Client" software. 

I want to get some files from windows 7 to my local computer. Therefore, I'm trying to share a folder. 

First of all, I opened a Terminal Service Client program. From the "Local Resources" tab I "added my local drive to the remote computer."

Later on, I was my hard drive of my local in "Computer" as "Local on x". I can open the x folder, but when I want to copy a file from Windows 7 to x, I'm confronting a problem. 

I'm getting an error and it says that:

"An unexpected error is keeping you from copying the file. If you continue to receive this error, you can use the error code to search for help with this problem.

Error 0x8007048F: The device is not connected"


Well, it is obvious that I cannot connect to my local machine from windows 7. 

How can I make it connect to my local computer?

Best regards...

---

### Post by pricetech on 2011-02-14
Samba ??  Tutorial here:

[http://ubuntuforums.org/showthread.php?t=1644585](http://ubuntuforums.org/showthread.php?t=1644585)

---

### Post by karpay on 2011-02-15
Dear pricetech,

First of all thank you for your reply.

I followed the instructions in the tutorial that you send but it did not seem to be worked.

Let me reexplain my problem. I'm connecting to the machine windows 7 remotely. But before I'm connect to windows 7 remotely, in the local resources tab, I checked the "Add my local drive to the remote computer." Please check the image below: 

[IMG]http://2.bp.blogspot.com/-nDFsobjIAMU/TVowAu2GvdI/AAAAAAAAACE/Ess724jZLCk/s1600/tsclient11.png[/IMG]

After I connect to the computer who has windows 7, I can see my local drive both under "Computer" and "Network"

Please check the image below:

[IMG]http://2.bp.blogspot.com/-rgYzjGd5DxA/TVox9XYH3HI/AAAAAAAAACI/QWpfF4NU0JA/s1600/tsclient2.png[/IMG]

But if I want to paste a file into my local folder I'm getting an error as shown in the image below:

[IMG]http://1.bp.blogspot.com/-n9x33nsnHoY/TVo3FZfYEYI/AAAAAAAAACM/L-kYxTvKhs4/s1600/theError.png[/IMG]

Any type of help is kindly appreciated.

Regards...

---

### Post by phatypus on 2011-02-26
same issue here.

---

### Post by BHEJU on 2011-02-26
Not expert. But it could be related to file system. As Win can not read ext file systems. You can try to install Ext2Fsd on win machine to make it able to read ext systems. 
May be this will work.

Cheers

---

### Post by ahouchens on 2011-11-29
Has anyone tried installing Ext2Fs to see if it corrects the issue?

---

