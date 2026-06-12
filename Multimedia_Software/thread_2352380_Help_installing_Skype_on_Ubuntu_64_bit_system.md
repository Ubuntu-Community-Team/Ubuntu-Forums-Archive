---
title: "Help installing Skype on Ubuntu 64 bit system"
date: 2017-02-11
forum: Multimedia Software
---

### Post by baloonatic on 2017-02-11
Okay so, I'm super new to using this sort of OS, so bear with me as I'm very much a layman. 
I went to the Skype website and they didn't have a 64 bit compatible installation method in their drop-down menu. 
I then googled a bit and found the following tutorial: [https://community.skype.com/t5/Linux/Ubuntu-14-04-LTS-64-bit-amp-Skype/td-p/3684533](https://community.skype.com/t5/Linux/Ubuntu-14-04-LTS-64-bit-amp-Skype/td-p/3684533)
However, upon completing step 1a, I recieved this response in the terminal:
> 
baloonatic@computername:~$ sudo apt-get remove skype skype-bin
[sudo] password for baloonatic: 
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing libautotrace-dev (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.


What's wrong, how do I fix this, and how do I get Skype on here?

---

### Post by Perfect Storm on 2017-02-12
*sudo apt-get remove skype skype-bin*
That you're doing with that command is to remove skype - is that you want?

---

### Post by Bucky Ball on 2017-02-12
Welcome. You can go to 'Software and Updates' and make sure you have the Canonical Partners repository enabled and then install Skype from the Software Centre or Synaptic Package Manager or whatever you're using. (Or in terminal as above but with 'sudo apt install skype'.)

Always check the official repositories before hunting for third-party sites. Safer that way and you can save yourself a lot of time. You don't need to do what you're doing. ;)

Which release are you using? Not sure that there is an official 64bit version of Skype for Linux anyway is there? The 32bit (i386) version works fine on 64bit and, as mentioned, is in the repositories. All you need to do is install it in a couple of clicks.

---

