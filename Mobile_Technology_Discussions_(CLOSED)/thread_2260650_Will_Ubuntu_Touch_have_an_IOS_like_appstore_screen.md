---
title: "Will Ubuntu Touch have an IOS like appstore screened on mallware by experts?"
date: 2015-01-13
forum: Mobile Technology Discussions (CLOSED)
---

### Post by White-Shark on 2015-01-13
Hello all,

I've read the news, this february Meizu will release the MX4 with Ubuntu Touch.

The Iphone iOS app store: Apple decide what the user is allowed to use. That's a disadvantage. But the advantage is, Apple checks all apps on mallware, ectc.

What I like to know; Will Ubuntu Touch also have an app store, where a apps are screened on malware, trojans, ectc., by a community of experts?

Allready thanx for the answers. ;)

---

### Post by ian-weisser on 2015-01-13
Considering that Ubuntu has had safe, secure software repositories for a decade,
and that those repositories are the easiest way to install software, 
and the Ubuntu's security model relies upon them, 
do you have any real basis to conclude that Ubuntu would abandon the highly successful concept ?

Go ahead, register at developer.ubuntu.com and try to upload some 'mallware'. See what happens.

---

### Post by White-Shark on 2015-01-13
I'm not a developer, not at all a tech-guy. But I've heard from experts linux is also very safe, because it has little marketshare. Googles Android -also linux based- is Microsofts Windows for smartphones. What I read is, it's less safe as iOS. And as iOS marketshare grows, it becomes also less safe.
So that's also why opinions and regulation by experts are important to me. ;)

---

### Post by grahammechanical on 2015-01-13
Ubuntu has a Software Development Kit (SDK) and developers are strongly encouraged to use it to write apps for the Ubuntu phone and tablet. The advantage to the developer is that the SDK makes it easy for them to submit an app for inclusion in the app store. And if they have followed the rules their app will be accepted in minutes.

A lot of thought has gone into making a Ubuntu phone secure. This is just the little I have heard about.

1) App developers have to create a Manifest. This is a list of authorisations or permissions that the app needs. If the developer includes in the manifest an action that could put the user at risk, then the app will be rejected. If the app is accepted then the manifest will be used to create an AppArmor profile. If the installed and running app then tries to do anything not in the AppArmor profile the app will be prevented from doing it.

2) If an app tries to access data used by other apps, then it will require user authentication for the action to proceed. For example, if a music app tries to access an email contact list it will require user authentication for that action to proceed.

3) Apps run in a sandbox or container. Apps cannot access the system space or the user space without authentication. An app with malware will be contained in the sandbox.

4) The file system is read only. Applications cannot make changes to the file system.

5) The phone OS has image updates not package updates as on the desktop. A comparison is made between the image in the phone and the updated image on the servers and the difference is downloaded. This means that downloads to update the OS will be small and the file system will remain read only.

6) The apt-get utility will not be available. We will not be able to download apps from anywhere but the app store. Applications from the internet are a security risk.

7) There is a special developer mode which will allow us to use apt-get to install software but once we start using that we will lose the ability to have image updates. Developer mode is a "use at your own risk feature." Developer mode is for developers to install their apps for testing on their phones. And if something breaks, then flashing phone is the only way to fix it.

I would not be surprised if using developer mode invalidated the manufacturer's warranty. If I was a supplier selling Ubuntu phones I would have a clause that specifically stated that using developer mode invalidated the warranty. I would refuse to refund the price of a broken Ubuntu phone if developer mode was activated unless it was a hardware fault. This is reasonable.

Oh, and I seem to remember a report about an app in the Apple app store that was malware. So, I would not be so confident of Apple security.

[http://www.computerworld.com/article/2483867/malware-vulnerabilities/researchers-outwit-apple--plant-malware-in-the-app-store.html](http://www.computerworld.com/article/2483867/malware-vulnerabilities/researchers-outwit-apple--plant-malware-in-the-app-store.html)

[http://www.engadget.com/2014/11/11/masque-attack-ios-exploit/](http://www.engadget.com/2014/11/11/masque-attack-ios-exploit/)

[http://www.wired.com/2012/07/first-ios-malware-found/](http://www.wired.com/2012/07/first-ios-malware-found/)

[http://www.theverge.com/2012/2/7/2782947/path-ios-app-user-information-collected-privacy](http://www.theverge.com/2012/2/7/2782947/path-ios-app-user-information-collected-privacy)

Regards.

---

