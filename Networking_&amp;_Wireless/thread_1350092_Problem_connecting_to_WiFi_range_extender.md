---
title: "Problem connecting to WiFi range extender"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by ultramarine13 on 2009-12-09
I have a EeePC 1000HD that just had Ubuntu installed today. And I am having problems connecting to the wireless range extender at home. This is not the first time I had the same exact problem with an Acer Aspire loaner from the shop that worked on it after a complete implosion of XP, so it isn't the computer, and the extender worked before the implosion, so I doubt it's that. So, on to the details.

When attempting to connect to the extender, the dialog box asking for the WEP code pops up. After entering the WEP code (correctly), it then pops up a window asking for the default keyring for the network manager. After guessing the keyring (it accepted password) it then attempted to connect for about 30 seconds before giving up and popping up the WEP code window again. It did the same thing if I denied the keyring for the network manager.

However, I am able to connect directly to the home modem. The problem is, the strength is very low from my room, and it isn't consistent. If I am opening more than one webpage, or if the page has multiple images, the transfer bogs down noticeably. And I don't bother with video. That was the whole reason for getting the extender in the first place. As for the hardware involved, the computer is a stock EeePC 1000HD running Ubuntu Netbook Remix (as mentioned), the modem is an older RCA broadband modem/router, and the extender is a Hawking wireless N range extender (WREN1 is the exact name, I think). Any help would be greatly appreciated.

---

### Post by diablo75 on 2009-12-09
Well a couple things come to mind...

If you are using WEP encryption you might try to enter the password in hexidecimal format instead of plain text.  If you set this password up yourself you should be able to get it from the extender where you originally entered the password.  It'll ask you to enter your passphrase, hit a "generate" button, and then you'll see the hex output that will look something like 1e34f32fbc323 or some gibberish like that.  Alternatively you can use a key generator [like this one]("http://www.andrewscompanies.com/tools/wep.asp") to create the hex version of the passphrase you used.

Also, when the system asks you to enter a keyring password, it's asking for the password that locks the keyring feature of Ubuntu that is responsible for saving passwords for things like wireless networks, SSH shares, email accounts to name a few things.  The purpose of the feature is to make it easier for you if you're the kind of user who goes between multiple networks with different passwords, so when you attempt to attach to one it asks your for your keyring password (which is always the same) to grant the system access to the actual password for that network and authenticate with it.  

Typically the keyring password is the same as the password you selected for your user account when you installed Ubuntu.  If you have your system setup to automatically log you into your account (so the login screen is skipped) it will ask you to enter your password.  If you disable automatic login, then the keyring will automatically be entered for you.  The keyring can also be cleared and setup so that it doesn't have a password at all, although this can be a security risk since anybody using the computer could turn it on and attach to a network you've saved a password for in your keyring without asking for further authorization.  Also, if you setup your keyring to store passwords without safeguarding its inventory with a password overtop, it will store passwords on your system unencrypted and anybody could open the laptop, then the file that stores these passwords and see them in plain text (meaning someone could steal your passwords).  [I wrote a blog about removing the keyring]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/") but it was intended for Ubuntu 9.04 so I don't know if it will work perfectly for Ubuntu Remix (I recall some comments being posted about it possibly not working, but it's worth giving it shot if that's what you want).

What I would do if I were you is go into System>Preferences>Network, click on the Wireless tab and clear all the entries out.  Then attempt to create a new profile for the network you are trying to connect to.  It will ask you to enter the WEP encryption password for your network, and then ask you to enter your keyring password to allow you to save that password to your keyring for future use.  Make sure you enter your accounts password for the keyring (since that is probably what it actually is) and hopefully it will work.

---

### Post by ultramarine13 on 2009-12-16
Thanks for the advice, diablo. I've been busy with school (finals and whatnot) so haven't been able to make time to fix the problem until now. I tried both of your suggestions, and neither one made a difference. It seems to me to be a problem in talking with the wireless extender, since it keeps trying to connect and not being able to. On top of that, password is no longer being accepted as the default keyring. As it turns out, the RCA connection is now fast enough (or maybe I'm being a little more patient), so I can stream videos, but the signal strength is still low. Any additional help would be appreciated.

---

### Post by chillyomi on 2009-12-16
Well maybe it just doesnt like you as would be my case

---

### Post by ultramarine13 on 2009-12-17
Well, that would be a problem, because this happened on another network, a public, unprotected network, and if I'm going to have hassles like this, maybe I'll have to switch back to XP. Which I kind of don't want, because I do like the openness of Linux.

---

