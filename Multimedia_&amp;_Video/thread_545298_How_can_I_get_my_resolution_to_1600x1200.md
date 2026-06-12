---
title: "How can I get my resolution to 1600x1200?"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by JohannesM on 2007-09-07
Hi everyone!

I'm a Ubuntu / Linux newbie and I was not happy to see that I could only add my resolution to 1024x768. I could not find any help from other threads for a solution because I don't understand all this xorg.conf file stuff. I tried editing it a little but it said that I don't have permission to edit it.

Now that's what I call a super OS!

If someone has any help that would be easy to do, reply asap!

Thanks in advance,
JohannesM :)

---

### Post by chrome307 on 2007-09-07
Hi there

There's some helpful tips here and it's step by step:

[http://ubuntuforums.org/showthread.php?t=531378](http://ubuntuforums.org/showthread.php?t=531378)

---

### Post by JohannesM on 2007-09-07
I'm sorry but I could not find any help from the link. Could you explain what information the thread holds?

Thanks,
JohannesM :)

---

### Post by chrome307 on 2007-09-07
You need to edit the Xorg config file and enter in your chosen resolution of 1600x1200 in the appropriate sections and then save the file - reboot.

---

### Post by JohannesM on 2007-09-07
For some reason I am not able to save changes made to my xorg.conf file when I edit it in the text editor. :(

---

### Post by hessiess on 2007-09-07
sudo dpkg-reconfigure xserver-xorg
or to edit manualy
sudo nano /etc/X11/xorg.conf

---

### Post by JohannesM on 2007-09-08
> **hessiess said:**
> sudo dpkg-reconfigure xserver-xorg
or to edit manualy
sudo nano /etc/X11/xorg.conf

Erm... That means?

---

### Post by beleth on 2007-09-08
Open up a terminal and copy/paste the code. The reason it isn't letting you save any changes is because you aren't opening the text editor as a root user.

sudo gedit /etc/X11/xorg.conf

It should prompt you for your password then open the file.

---

