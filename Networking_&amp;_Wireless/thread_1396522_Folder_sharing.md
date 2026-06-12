---
title: "Folder sharing"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by dalitrel on 2010-02-02
Hi there,

I am very much a newbie, having recently switched from Windows to Ubuntu.

I have one desktop and one laptop. Both run Ubuntu 9.10, with Nautilus 2.28.1.
The desktop has folders containing a large number of photos and I would like to be able to see them from the laptop.

From the desktop, I have right clicked on the relevant folder to find the "sharing options". This prompted me to load and install Windows Shares. So far so good. The folder icon now has an "open hand" symbol under it.

If I now login as a different user on the desktop, or login on the laptop and click on "network" (within Places), I can see my desktop.

If I click on the desktop icon, I can also see the newly shared "Photos" folder.

However, if I try and open this Photos folder, I get a prompt:

"Password required for share photos on desktop"

There are then 3 fields:
Username (filled in automatically)
domain: WORKGROUP
password:

Now I have tried entering every password I can think of (mine, other users such as my wife's or my son's...) but none are recognised.

Is there a default password that I should be aware of?

The "Shared Folders Administration Tool" manual refers to the administrator password, but I do not remember setting any other password but my own.

Help!!!!

---

### Post by suseendran.rengabashyam on 2010-02-02
Hi,

When you get the prompt asking for the "Username:" and "Password:" you need to enter the correct user name and password of the account which is present in your Ubuntu Desktop. Let me know if it works.

---

### Post by dalitrel on 2010-02-02
hmmm... If, from my wife's account I click on "network" (within Places), I can see an icon for my PC.

If I click on that icon, I can also see the new shared "Photos" folder.

However, if I try and open this Photos folder, I get a prompt:

"Password required for share photos on desktop"

There are then 3 fields:
Username (filled in automatically with my wife's username)
domain: WORKGROUP
password:

I have tried to put in her or my password in there (incidentally, our passwords are the same), but it does not work and the prompt comes back.

---

### Post by Morbius1 on 2010-02-02
Did you create the share allowing guest access? If so it should not be asking for any password.

Please post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

If you allowed guest access the output of net usershare info should look something like this:
> [winj]
path=/windows/Photos
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]guest_ok=y[/COLOR]


---

### Post by Morbius1 on 2010-02-02
If you specifically wanted to restrict access to the share then you have to create a local account on your machine for your wife followed by a samba password for that account. For example:

Let's say your wife's user name is Mary:

Open **Terminal**
Type **sudo useradd -s /bin/true mary**

[COLOR=Blue][I]This will create a linux user on the server that has no server logon 
[/I]*capability and no server home directory.*[/COLOR]

Type **sudo smbpasswd -a mary**

[COLOR=Blue]*This will create and enable the password that Mary will use to access that share.*[/COLOR]

---

### Post by dlabelle11 on 2010-02-02
Try username root and then what ever you set your root passowrd too ... its worth a try... you can set your root password under system -> administration -> users and groups....and then it says click to make changes.... click it enter your curent account password or admistrator password.... then you should be able select and set the root password...

good luck

---

### Post by suseendran.rengabashyam on 2010-02-03
Hi,



1. The username & password that you need to use to be able to  access a remote share are those of the remote user who has created the  share. Your local username & password do not help you connect to the  remote share. Leave the "Domain" setting as it is.
       

2. With "Allow others to create and delete files in this folder"  checked, while creating the share, the credentials that would work are  those that are related to the users on the remote system.
       

3. With "Guest access (for people without a user account)" checked,  while creating the share, anybody would be able to access the share  without providing a username/password.
       

Let me know if this helps.

---

