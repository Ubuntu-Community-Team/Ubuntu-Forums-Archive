---
title: "Why empathy is so dependece on the keyring-daemon?"
date: 2010-06-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-26
As you can see in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/569667](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/569667)
if i disable the option to enter password after log off i get:
"Error communicating with gnome-keyring-daemon" when i open seashore and then 
if i open empathy it doesn't have accounts there and it cannot import accounts from pidgin 
pidgin however is still working fine because he doesn't depend at all on keyring-daemon.

But i do enable the option to enter password after log off the keyring-daemon is working fine.

And by the way normal auto login in boot is causing no problem just auto login in the log off window.

Thanks in advance.

---

### Post by Reiger on 2010-06-26
Empathy depends on the keyring tool to store your credentials in an attempt at secure storage; whereas Pidgin stores your credentials in plain text and doesn't bother with the whole security thing.

---

### Post by LKjell on 2010-06-26
> **Reiger said:**
> Empathy depends on the keyring tool to store your credentials in an attempt at secure storage; whereas Pidgin stores your credentials in plain text and doesn't bother with the whole security thing.

You can still retrieve the password if you know the login password.

---

### Post by gnomeuser on 2010-06-26
> **LKjell said:**
> You can still retrieve the password if you know the login password.

Kinda beats being able to read it in plain text at will :)

---

### Post by aviramof on 2010-06-26
Basically empathy is a useless software to any one who is using any sort of auto login because he ask for password when you open it.

---

### Post by DoeRayMe on 2010-06-26
i just use a empty password for my keyring, as im the only one using my pc and i dont get asked anything, and i use auto-login

---

### Post by aviramof on 2010-06-27
Thanks.

---

### Post by TerminX on 2010-06-27
> **Reiger said:**
> Empathy depends on the keyring tool to store your credentials in an attempt at secure storage; whereas Pidgin stores your credentials in plain text and doesn't bother with the whole security thing.
Pidgin stores passwords in plain text because Pidgin has no business depending on something like gnome-keyring-daemon as it's not solely a GNOME app, and implementing their own encryption would be absolutely worthless as whatever is needed to decrypt would be right there in the program source.

If someone with malicious intent is able to access your ~/.purple/accounts.xml in the first place you've already failed at security and allowed yourself to be compromised.  It's better to leave things in the open than pretend they're secured. :p

---

### Post by aviramof on 2010-06-27
If ubuntu is indeed secure then no one should be able to access my ~/.purple/accounts.xml file so even using an empty keyring password is good enaf especilly 
if your a sole user on the box.

---

### Post by gnomeuser on 2010-06-27
> **TerminX said:**
> Pidgin stores passwords in plain text because Pidgin has no business depending on something like gnome-keyring-daemon as it's not solely a GNOME app, and implementing their own encryption would be absolutely worthless as whatever is needed to decrypt would be right there in the program source.

If someone with malicious intent is able to access your ~/.purple/accounts.xml in the first place you've already failed at security and allowed yourself to be compromised.  It's better to leave things in the open than pretend they're secured. :p

gnome-keyring and kwallet developers have formed a DBus standard called secrets so this is cross desktop, or rather will be once both projects fully implement and deploy support. 

You are also forgetting that other applications have access to your .purple/accounts.xml without asking for permission. With a keyring they would have to. You are forgetting several attack vectors such as malicious or malfunctioning applications.

---

### Post by aviramof on 2010-06-27
I discovered one more problem when i tried to shut down the computer i got a message that the keyring  is still running and what do i want to do do i want to shut down any way and etc.

If that would happen every time when i want to shut down the computer without closing empathy  before then it's not good and it could be another reason why not use emapthy.

---

### Post by Mr. Picklesworth on 2010-06-27
> **TerminX said:**
> Pidgin stores passwords in plain text because Pidgin has no business depending on something like gnome-keyring-daemon as it's not solely a GNOME app, and implementing their own encryption would be absolutely worthless as whatever is needed to decrypt would be right there in the program source.

Actually, these things should (and generally do) use one-way encryption. The reason gnome-keyring needs your password to be unlocked, the reason why websites can't just email you your password (and if they can you should be afraid), and the reason why free software can encrypt things, is they are incapable of deciphering your data without your secret key.

Same way packages are digitally signed.

For a taster of what I'm babbling about, try echo "Test" | sha512sum in a command line :)
It's impossibly difficult to figure out what string created that output, but you can figure out a given string is the same by feeding it in to that same function.



aviramof: gnome-keyring-daemon is meant to be invisible. As said, it always needs your password to be unlocked (because its contents are properly encrypted), but it only needs to be unlocked once and this can happen at the same time you log in if you are entering your password to do so. If it is not invisible, that is a bug to be reported.

---

### Post by TerminX on 2010-06-27
> **Mr. Picklesworth said:**
> Actually, these things should (and generally do) use one-way encryption. The reason gnome-keyring needs your password to be unlocked, the reason why websites can't just email you your password (and if they can you should be afraid), and the reason why free software can encrypt things, is they are incapable of deciphering your data without your secret key.
Excuse me, I'm not some idiot who doesn't know how cryptographic hashing functions work, but even if I was, hashing has absolutely **nothing** to do with the topic of my post, which was storage of passwords *in an IM client*.  

Clearly, an IM client must store passwords in such a way that the original string can be returned and used to log in an account.  In fact, this is a situation where a one-way cipher would **never** be used, ever, as it would entirely defeat the purpose of storing the password in the first place.  Pidgin could implement its own password vault functionality similar to that of the GNOME keyring, but once again that would entirely defeat the purpose of Pidgin storing passwords in the first place: logging in without user intervention.

In the future, it might be a good idea to ask yourself if what you're about to post even applies to the situation at hand before going out of your way to talk down to people in an attempt to explain it.

---

### Post by Absolom on 2010-06-27
I tried using my password that I set when I installed ubuntu but the keyring doesn't accept it and I have no idea what password it is expecting. What good is security if it locks out the only user on the system?

I can log in and use anything except those programs that want kwallet or keyring

---

### Post by Mr. Picklesworth on 2010-06-27
> **TerminX said:**
> Excuse me, I'm not some idiot who doesn't know how cryptographic hashing functions work, but even if I was, hashing has absolutely **nothing** to do with the topic of my post, which was storage of passwords *in an IM client*.  

Clearly, an IM client must store passwords in such a way that the original string can be returned and used to log in an account.  In fact, this is a situation where a one-way cipher would **never** be used, ever, as it would entirely defeat the purpose of storing the password in the first place.  Pidgin could implement its own password vault functionality similar to that of the GNOME keyring, but once again that would entirely defeat the purpose of Pidgin storing passwords in the first place: logging in without user intervention.

I'm not trying to talk down to anyone.

To me, your post sounded as if you were innocently unaware of the magic of modern cryptography. I read it as &#8220;anything can be decrypted instantly if you know the encryption algorithm.&#8221;
So, I saw fit to provide an innocent little introduction, even if only vaguely related. Not just for you, but also for innocent bystanders who take &#8220;whatever is needed to decrypt would be right there in the program source&#8221; as what I thought it sounded like.

Obviously I was wrong to that end. Great!

Indeed, now it's all jammed into my head, I understand what you mean in the context of Pidgin alone. It implementing its own secret key stuff *would* be pretty pointless and horrible. There is a [feature request on their end]("http://developer.pidgin.im/ticket/673") to use whatever password storage system is native to the platform it's running on, but they aren't keen on the extra maintenance of having a bunch of #ifdefs. Makes sense; they want a platform-neutral layer that does that bit. I hate #ifdefs, too :)

---

### Post by aviramof on 2010-06-28
> **Mr. Picklesworth said:**
> 
aviramof: gnome-keyring-daemon is meant to be invisible. As said, it always needs your password to be unlocked (because its contents are properly encrypted), but it only needs to be unlocked once and this can happen at the same time you log in if you are entering your password to do so. If it is not invisible, that is a bug to be reported.

The fact is that it's not invisible because i use auto login so i don't enter password at boot process and i don't think that a lot of people who are the sole user of a private not mobile computer  who knows a thing or two would choose to enter 
password every time they start there computer,they would all use auto login at boot and to be honest i have never come across an IM client that require you to enter a master password so that you can access the other passwords of your 
accounts.

In all the IM software that i ever  used which are icq,msn,yahoo ,msn,AOL,Miranda,trilian,Google talk and everything else you can think of the encryption is in the software saving its passwords in a file that if open by notepad and etc the content 
is jumbled and etc,granted there are software like nirsoft softwares that can decipher that(i don't think they work in linux)but it's not a simple text file that everyone can read any way.
[http://www.nirsoft.net/password_recovery_tools.html](http://www.nirsoft.net/password_recovery_tools.html) 

So the fact that empathy is using a master password from the OS itself and if you use auto login the only way to get rid of this problem is by setting empty password for keyring and use unsafe storage this is all sound a bit ridiculous to me 
i mean how many softwares are currently using keyring to store there password apart from empathy today? so this entire system is in place right now for the sake of one IM software. 

And say in the future there would be more softwares like this as long as i use auto login and i don't think that i will ever stop using auto login i would still use unsafe storage so the keyring would loose it's entire purpose completely,all it does right 
now it's to cause me to use non keyring softwares like pidgin or to just use unsafe storage and that it.

So if the password protecting keyring system can't do its job without a master password it is quite useless,not to mention that if you use total auto login meaning disable the need to enter password even in the windows that appear after login off 
from users-admin software which is a valid option there then the keyring-daemon is stop working all together and i have a bug report that i posted to prove it you can find it in launchpad. 

So basically i really don't understand why i need the keyring system at all if any one have more reasons for it that i don't know about them then i would be happy to hear about that.:)

---

### Post by LKjell on 2010-06-28
The safest place you can keep your passwords are in the brain, till someone figures out a way to read your brain.

This article should shed some lights on security. [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Either you have autologin with a blank keyring password is the same with a password entered login with a keyring password when you already entered.

---

### Post by aviramof on 2010-06-28
I do know my passwords by hart but i am not about to enter them every time for each account the point is that for a single user with auto login the keyring is useless period.

---

### Post by ranch hand on 2010-06-28
> **aviramof said:**
> I do know my passwords by hart but i am not about to enter them every time for each account the point is that for a single user with auto login the keyring is useless period.
I am the only user on this box but I use a login and do not have this problem.

Auto login just bothers me.  The idea that anyone can boot the box is just not real good.  Yes I realize that anyone with a little knowledge of Linux can get in, but it will take some time so the possibility of getting interupted is much greater.

When you use the login screen you also have other options available that are not if you use auto login unless you use the timed login so that the screen shows.

Why not just log in?  I have never understood how folks can do the auto thing at all.  Even my Dreaded Mother in Law has her MS computer set up with a password and no I had nothing to do with that it is just the way she wants it.  I think she is right.

---

### Post by aviramof on 2010-06-28
I have my own computer there is no one that can excess it but me, and i don't understand what do you mean "it will take some time" i choose auto login when i install
ubuntu somewhere during the install process when you choose your name and password you can change it to auto login and that it.

And beside even via Ubuntu it's easy all you need to do is to activate gdmsetup and set it there.

And what other options?the option to choose between gdm and kdm and and etc if i have something like this installed? i can do that via the log off screen or i can set the default via gdmsetup 

And maybe your  Mother in Law doesn't know that she can do it it's a bit complected there
(start-run-type control userpasswords2 and disable the need to enter user name and password)or that a lot of people have access to her computer that is why she use it,but me i prefer to start 
the computer go do something then go back and everything is ok.

In windows i even have scheduled tasks and startup shortcuts that opens the browser at home page and etc so that i want have to do it all the time.

Auto login and auto everything can be quite nice once you get use to it.

---

### Post by ranch hand on 2010-06-28
If you have the login screen come up you have the option of what session to log into.  Gnome, failsafe-gnome, xterm, and any other DE you may have installed.  These are awful handy particularly on a testing OS.

There is no way that I, or the Dreaded Mother in Law, want to have auto login.

---

### Post by aviramof on 2010-06-28
Since i don't have other DE it is not useful enaf so that i would use keyring password and login with a password auto login is a lot more comfortable 
once you get used to it then to go back and start typing password every time you start the computer and then wait for it to finish loading everything.

And speaking of it i think that perhaps it's might be a good idea to add failsafe-gnome to the grub menu since recovery mode is not always work the way that it should.

---

### Post by Mr. Picklesworth on 2010-06-28
> **aviramof said:**
> The fact is that it's not invisible because i use auto login so i don't enter password at boot process and i don't think that a lot of people who are the sole user of a private not mobile computer  who knows a thing or two would choose to enter 
password every time they start there computer,they would all use auto login at boot and to be honest i have never come across an IM client that require you to enter a master password so that you can access the other passwords of your 
accounts.

If you want, you can always open Passwords and Encryption Keys (seahorse) under Accessories. Under the Passwords section right click the login keyword, choose Change Password, enter your current password and leave the new password field blank. Voila! No encryption; it is always unlocked.

---

### Post by aviramof on 2010-06-28
I am aware of that option and that is what i did when i decided to use empathy again but still i don't understand why empathy don't have it's own password encryption and need to OS for help.

---

### Post by Mr. Picklesworth on 2010-06-28
> **aviramof said:**
> I am aware of that option and that is what i did when i decided to use empathy again but still i don't understand why empathy don't have it's own password encryption and need to OS for help.

Ah! That's what TerminX was talking about earlier, but I kind of misread it in a noisy fashion. I guess others could do the same :)

It's unreasonable for Empathy to encrypt passwords on its own, because this kind of encryption relies on a password that only you know. (If it didn't use a secret key, its only line of defence is obscurity).

So, if Empathy did that itself, you would have to enter your password for Empathy's auto-login to work. NetworkManager would have to do the same, so you would be entering your password to decrypt passwords for two pieces of software already. Many others follow.

With a keyring daemon, you only need to enter your password *once* to &#8220;unlock&#8221; it and all those applications have access.

---

### Post by aviramof on 2010-06-28
I meant that like other software such as icq,msn miranda and etc who don't need something like the keyring it could encrypt it in an unreadable profile file and that it.

---

### Post by zekopeko on 2010-06-29
> **aviramof said:**
> I meant that like other software such as icq,msn miranda and etc who don't need something like the keyring it could encrypt it in an unreadable profile file and that it.

And how would ICQ or Miranda know what was your password?

---

### Post by aviramof on 2010-06-29
Forget about it we are talking about two completely different methods i guess.

---

