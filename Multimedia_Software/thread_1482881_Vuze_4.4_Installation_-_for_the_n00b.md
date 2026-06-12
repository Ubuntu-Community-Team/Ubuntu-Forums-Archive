---
title: "Vuze 4.4 Installation - for the n00b"
date: 2010-05-14
forum: Multimedia Software
---

### Post by DeadlyOats on 2010-05-14
I want to install Vuze version 4.4, which I will download from [http://www.vuze.com](http://www.vuze.com).  I want to install it in the proper directory, and I want to do it correctly.  In the past, I just unpacked the compressed file in any directory - that ***let*** me do it - and that was that.

However, *this time*, I want to put Vuze in the correct directory where applications _should_ go.  I use Ubuntu 9.10.  So....  Which *is* the correct directory that I *should* use to install Vuze 4.4?

After I've properly install Vuze 4.4 in the correct directory, I want to properly create an entry for Vuze in the Applications/Sound & Video/ menu with Vuze's _proper icon_ - which _I don't know_ how to locate (the icon, I don't know how to properly locate the icon for the app  when creating the entry.....  So I end up using whatever icon is see....  Sad... I know... :oops:).

I am a point-and-click-gui-end-user.  As such, I've found that if I need to install apps, or look at technical stuff, I'm always denied access, because I don't have the appropriate permissions to do so....  So.... 

Someone, among you Linux Gurus, is gonna tell me in which directory I should install Vuze, but I won't know *_how_* to install it *there*, because I will be _*denied*_ permission.....  So... _How_ do I get the proper permissions to install Vuze 4.4 in the proper directory (whatever that directory turns out to be)?

I consider myself to be a proficient point-and-click-gui-end-user, but I totally suck at command-line stuff, and if I need permissions to do stuff, I don't know how to get it.

So, if you can step-by-step your instructions to me - even if it's all command-line stuff, I will appreciate it, and will faithfully follow your instructions.  Yes, I will - most carefully follow your step-by-step instructions...  So, please be gentile... :oops: :redface:

Seriously, I'm not at all command-line oriented, so you really need to step-by-step it for me. :oops:

I thank you all, profusely, for your indulgence to my totally-uber-n00ber request.

---

### Post by BoneKracker on 2010-05-14
/usr/local/bin

Begin commands that require elevated permissions with the word sudo.


If the application is for your own personal use (not used by other users of your system), and the application does not require elevated privileges to run, then there's really nothing wrong with what you did (just plopping it in your home directory).

---

### Post by DeadlyOats on 2010-05-14
Thanks for your reply, BoneKracker.

If I try to drag and drop the package into /usr/local/bin, I am denied permission.

(I tried using the sudo command, but I kept getting errors, I ended up using sudo -l -U my-username, but I was still denied permissions to drag and drop the package into /usr/local/bin.  (Of course, it didn't work, but I had to try it - you never know.....))

So, at the command-line prompt, I enter sudo, and that will give me the permissions I need to run commands that need them.....

So....  What commands do I enter after sudo to get Vuze_Installer.tar.bz2 to unpack and install in /usr/local/bin?

Then, where do I locate Vuze's icon, so that I can use it to create an entry in the Applications>Sound & Video menu?

---

### Post by BoneKracker on 2010-05-14
> **DeadlyOats said:**
> Thanks for your reply, BoneKracker.

If I try to drag and drop the package into /usr/local/bin, I am denied permission.

(I tried using the sudo command, but I kept getting errors, I ended up using sudo -l -U my-username, but I was still denied permissions to drag and drop the package into /usr/local/bin.  (Of course, it didn't work, but I had to try it - you never know.....))

So, at the command-line prompt, I enter sudo, and that will give me the permissions I need to run commands that need them.....

So....  What commands do I enter after sudo to get Vuze_Installer.tar.bz2 to unpack and install in /usr/local/bin?

Then, where do I locate Vuze's icon, so that I can use it to create an entry in the Applications>Sound & Video menu?

First of all, I hope you first checked for vuze in the ubuntu package repository.  As I understand, it's what they used to call Azureus, and I can't imagine they don't have it.

If they have it, even if it's not the very latest version, that's what you should be using, since it's been "ubuntu-ized" by the Ubuntu packagers.  In linux, you're better off not just installing random crap off the internet like you do in Windows (or you'll end up with a buggy system like Windows).

But if you absolutely must install this off the internet...

```

# copy the installer archive to the location, for simplicity
sudo cp Vuze_Installer.tar.bz2 /usr/local/bin

# go there yourself
cd /usr/local/bin

(read "man cd")

# check to see it actually got moved there
ls

(read "man ls")

# unpack the installer archive
sudo tar -xjf Vuze_Installer.tar.bz2

(you can just type sudo tar -xjf Vuz<TAB> and it will complete it for you)
(read "man tar")

# make the files all owned by root
sudo chown -R root: <whatever folder name it created>

(read man "chown")

#Then cd into whatever folder it created
cd vuze (or whatever)

# Read any files called README, INSTALLATION, INSTALL, etc.
ls

less README
(q to exit)

less INSTALLATION
(q to exit)

# If that doesn't tell you what to do, see if there's an installer script, probably would end in ".sh"
ls

(you might have to hunt for it)

# if there's an installer script
sudo ./install.sh
(or whatever)

# really, you should go through and check all the file permissions to make sure they're safe.  This is something your distro's packagers and security people do for you, but since you're installing it free-ball style, off the internet, you have to do it yourself.  Since you don't know what you're doing, you will have to skip this step.

# locate the binary that starts the application
(it's probably /usr/local/bin/vuze/vuze or something)
(that's what you're going to want to put in your desktop "icon"
(test it first by trying to execute that command from the terminal and see if it starts)

```

Search your computer for an icon.  This is something else your distro's packagers would have already taken care of for you, if you had just installed it from the ubuntu package repository.  But since you're free-balling it, you'll have to see if there's one in the vuze directory or see whether the installer put one somewhere else.

If you can't find it, then, go to your web browser, and google for "vuze icon".

I recommend you just install whatever version Ubuntu is currently providing (I assume they do).  I don't use Ubuntu so I wouldn't know.  The hazards of installing off the internet are probably not worth it just to have the latest version.

---

### Post by erlitzki on 2010-06-19
Maybe this will help: [http://www.detector-pro.com/2010/05/install-vuze-on-ubuntu-10-04.html](http://www.detector-pro.com/2010/05/install-vuze-on-ubuntu-10-04.html).

---

