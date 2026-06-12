---
title: "How To: Definitive Samba Guide for 10.04 (probably 9.10 too)"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by d00derino on 2010-05-01
When I first started messing around with Ubuntu, Samba was one of the first things I wanted. The guides posted here are both outdated, don't work, and overly complicated. It took me about 2 hours of custom work and messing around to do. 

Last night I installed 10.04 with a fresh install, and I went to one of the Samba threads here that I used with 9.10. Doesn't work, filepaths are incorrect, and the template given for smb.conf is wrong. I googled it, and I got [this link](http://www.jonathanmoeller.com/screed/?p=1590&cpage=1#comment-9376). Much easier and cleaner, and worked the first time through. 

> Ubuntu 10.04 Lucid Lynx has come out, and that means it&#8217;s time to explain how to do a basic Samba setup on the new version. All Terminal commands in this walkthrough are bolded, and USERNAME stands for your username on your Ubuntu system.

First, you&#8217;ll need to install Samba. Fire up a Terminal window and use this command:

**sudo apt-get install samba**

Follow the default prompts to install Samba. Now, Samba uses a separate set of passwords than the standard Linux system accounts (stored in /etc/samba/smbpasswd), so you&#8217;ll need to create a Samba password for yourself with this command:

**sudo smbpasswd -a USERNAME**

(USERNAME, of course, is your actual username.)

Type a suitably strong password (make sure it includes uppercase, lowercase, punctuation, and numbers). Once your password is created, the next step is to edit your /etc/samba/smb.conf file, the configuration file for Samba. Begin by creating a folder named &#8216;test&#8217; on your home folder; we&#8217;ll use that for our test shared folder (you can create other shared folders using the same method):

**mkdir /home/USERNAME/test**

Next, make a safe backup copy of the original smb.conf file to your home folder, in case you make an error:

**sudo cp /etc/samba/smb.conf ~**

Now use your text editor of choice to edit smb.conf:

**sudo gedit /etc/samba/smb.conf**

(New users will probably find gedit the easiest to use due to its GUI; but you can use emacs or vi just as readily, especially if you&#8217;re using the server version of Ubuntu, which doesn&#8217;t include X11 by default.)

Once smb.conf has loaded, add this to the very end of the file:

[B][test]
path = /home/USERNAME/test
available = yes
valid users = USERNAME
read only = no
browsable = yes
public = yes
writable = yes[/B]

(There should be no spaces between the lines, and note also that there should be a single space both before and after each of the equal signs.)

These settings will share the test folder we created earlier, and give your username and your username alone permission to read and write to the folder. Once you have input the changes, save smb.conf, exit the text editor, and restart Samba with this command:

**sudo restart smbd**

Once Samba has restarted, use this command to check your smb.conf for any syntax errors:

**sudo testparm**

If you pass the testparm command, Samba should be working; try accessing the shared folder from another computer on your LAN.

-JM

I'll note one major difference from the 51 page thread here on Samba. You DO NOT need to create a separate Samba user for the computers you want to connect to the Samba share. You can, and restrict read/write abilities, but by this tutorial, you connect using the USERNAME credentials. 

If anyone wants to append anything here, like WINS support, or adding users so that you can disable gust access, or go into detail with chmod options, feel free. This is a great beginning step to Samba, and I'd love for this topic to chronicle the more advanced things you can do with it after you got your starting point ready.

---

### Post by Dimoutlook on 2010-05-02
Great guide works perfectly Thank you

Dimoutlook:popcorn:

---

### Post by WolfRage on 2010-06-05
I figured it out, sorry but I believe my way is easier and I just want to spread the word. Please see here: [http://ubuntuforums.org/showthread.php?t=1502265](http://ubuntuforums.org/showthread.php?t=1502265)

---

### Post by d00derino on 2010-07-11
I get where you're coming from with GUI being the easiest solution, but from what I've found it seems that it doesn't work as faithfully as the terminal way. 

Trust me, I have tried it GUI-wise too.

---

### Post by TruViet911 on 2010-09-25
thanks alot. it works like a chamr

---

### Post by riffin-rich on 2010-11-06
d00derino, thanks so much for posting this "how to" Samba guide; the process you outlined worked perfectly for me on the first try!  Instead of connecting to /home/username/test, I have it connecting to /home/username, so I can get to all of my stuff.  That said, I do still need help with two issues that I'm hoping someone can help me with.

EDIT (resolved):  I have a second hard drive, /dev/sdb, which is mounted in a removable tray, and it is named "2TB-Backup" ... I figured out how to add that as another share.  Right below the [home] section provided by d00derino, I added the following section:

[HDD2]
# To mount the drive, /dev/sdb, named "HDD2"
path = /media/HDD2
volume = 2nd HDD
available = yes
valid users = yourusername
read only = no
browsable = yes
public = yes
writable = yes

Also, under the section named ####### Authentication #######, I also uncommented the line, security = user to require my linux user account log-on for access.


Something I can use help with is that my Mac OS X displays two, back-to-back, pop-up windows for 0.5 seconds each ... something about asking me if I want to allow the Finder.app to allow incoming connections.  On my Mac OS X firewall, I did set it to allow incoming connections for smbd because on occasion, I connect to it via samba from other systems.  I also enabled nmbd to allow incoming connections, but it didn't help.  Not sure if I need it to accept incoming connections...?

Thanks so much!  I scoured a dozen posts before finding this one ... glad I didn't go with simple file sharing.  Thanks again! - Rich

---

### Post by Dennis Primm on 2011-08-22
OK guys, I'm an idiot, so can you please help me out here???

Everything was working AOK until I got to the password part.  I entered my password and then entered it a second time (for confirmation) and it gave me an error (I wish I hadn't closed the terminal window now!!! See what I mean?  I'm a dumba_ _ !!!) that it didn't add it for USERNAME.  I then tried it again entering my password with using my USERNAME (password separated by a space and then username).  After that didn't take, I entered the command (**sudo smbpasswd -a USERNAME) **again and entered my password without a space and then my username that didn't work either, so where do I go from here?

I forgot to mention that I'm running 11.04.  Does that make a difference?  Additionally, I've got "File Sharing", "Personal File Sharing", and "Giver" packages installed on my system.  I still can't share files with my Dad's computer.  We are linked through a Netgear router.

I'd sure appreciate your help on this one.

Thank you,

Dennis S. Primm

---

### Post by Dennis Primm on 2011-08-22
I forgot to mention that I'm running 11.04.  Does that make a difference?

---

### Post by mikewhatever on 2011-08-22
It's real simple.
1. Copy/paste the following command into a terminal (with your username), and hit enter:
```
sudo smbpasswd -a USERNAME
```

2. Type the password, and hit enter.

3. Retype the password and hit enter.

PS: Don't add or remove spaces or other characters anywhere.

---

### Post by Dennis Primm on 2011-08-22
I just opened the terminal again and entered the command you gave me and then I typed in my password and it returned "Sorry, try again."  I then tried again and it responded with the same thing.  Should I go back and start from the beginning?

Thank you so much for your assistance!

Sincerely,

Dennis

---

### Post by Dennis Primm on 2011-08-22
Please note I'm not using the same password that I use to login to Ubuntu.  And I was following the instructions given by d00derino.

Here's exactly the mess I'm in now...

[sudo] password for dennis: 
Sorry, try again.
[sudo] password for dennis: 
Sorry, try again.
[sudo] password for dennis: 
Sorry, try again.
sudo: 3 incorrect password attempts
dennis@ubuntu:~$ Sorry, try again.
Sorry,: command not found
dennis@ubuntu:~$

---

### Post by Dennis Primm on 2011-08-22
THe password I was entering appears as: Lxxxxx123 (where the x's are other lowercase letters)...

I don't know why that wouldn't work.

---

### Post by capscrew on 2011-08-22
> **Dennis Primm said:**
> THe password I was entering appears as: Lxxxxx123 (where the x's are other lowercase letters)...

I don't know why that wouldn't work.

Let's see what is in the Samba users database.  Post the output of the following ```
sudo pdbedit -L
```

---

### Post by mikewhatever on 2011-08-22
It looks like you've already set the password for that user. Try **sudo smbpasswd -x USERNAME** before the above.

---

