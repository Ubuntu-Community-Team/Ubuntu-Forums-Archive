---
title: "SCIM icon disappeared from sys tray"
date: 2009-07-18
forum: Multimedia Software
---

### Post by varunbhatbm on 2009-07-18
From last week, I'm not able to see SCIM icon in system tray. 
If I start SCIM manually in terminal, I can see SCIM icon, but the behaviour is strange. I get the menu on right click on SCIM icon, but I don't get list of languages when I left click on it.
I uninstalled SCIM and reinstalled, the problem persists. 

Please help me with this. I need SCIM to load when I start ubuntu and list of languages should appear when left click on the icon.

---

### Post by mhenriday on 2009-07-19
**Varunbhatbm**, after updating to **Firefox 3.5.1** (**3.5.1+build1+nobinonly-0ubuntu0.9.04.1**), I'm seeing a similar phenomenon - while the **SCIM** icon _is_ displayed on my top panel, I can no longer use it to imput CJK languages, Russian, etc. I'm also running an earlier version of the **Swiftweasel** browser (**3.5b4**) ; there **SCIM** works precisely as it should, so it would seem that the problem is connected to the Firefox update. The version of **SCIM** I have installed, **1.4.7-3ubuntu12**, is, according to Synaptic, the latest available. I've been unable to find any further information on the [**_[COLOR="Blue"]SCIM site[/COLOR]_**]("https://sourceforge.net/apps/mediawiki/scim/index.php"), which is under renewal. Any other users who've observed this phenomenon ? Any suggestions as to how to get **SCIM** to work with the latest **Firefox** update ?...

Henri

---

### Post by varunbhatbm on 2009-07-20
> **mhenriday said:**
> **Varunbhatbm**, after updating to **Firefox 3.5.1** (**3.5.1+build1+nobinonly-0ubuntu0.9.04.1**), I'm seeing a similar phenomenon 

Thanks for the reply Henri.
Is there are way to revert back the Firefox update ? I dont use too many features of Firefox and I dont want to trouble SCIM for firefox features.

---

### Post by mhenriday on 2009-07-25
**Varubhatbm**, rather than going backward and uninstalling **FF 3.5.1**, why not go forward and install **FF 3.5.2pre** instead, which in my experience works very well with **SCIM**, as can be seen in the attached screenshot ? You can get it as a **Launchpad** ppa ; to do so, click «System» &#8594; «Administration» &#8594; «Software Sources», open the «Third Party Software» tab, click the «Add» button in the lower left-hand corner and insert the following in the box that then opens :
> deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/Ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/Ubuntu) jaunty main

When the above has been done, you can run
```
sudo apt-get update
``` after which the latest 3.5.2pre build will be installed (you can check by searching for «firefox» in «Synaptic», you should see both the standard 3.5.1 version and the new 3.5.2 build). The browser package will be placed under > /usr/lib/firefox-3.5.2pre To access the browser you will have to edit your applications menu (right-click «Applications» and choose «Edit menus», click «Internet» in the left-hand panel and then «New object» in the right hand panel. A small window called «Program start properties» will then open, with three boxes to be filled in ; to the right of «Name» you can enter «Mozilla Firefox 3.5.2» (without the quotation marks), to the right of «Command» ```
/usr/lib/firefox-3.5.2pre/firefox-3.5
``` and in the box for «Comment»you can enter what you wish - I have «Mozilla Firefox 3.5.2pre». Close the window and the main menu window ; you should now be able to load the browser by clicking «Applications» &#8594; «Internet» &#8594; «Mozilla Firefox 3.5.2». You can also put a button on your top panel by right-clicking «Mozilla Firefox 3.5.2» and choosing that option from the menu that then appears....

A little work, admittedly, but to my mind it's worth it to get **SCIM** working again !...

Henri

---

### Post by varunbhatbm on 2009-07-25
Thanks for the reply Henri.
I followed the steps u mentioned, but still can not get my SCIM working. 
I installed 3.5.2Pre and started firefox. When I click on the SCIM icon, still dont get list of languages. :( 
Please let me know, if I'm missing something.

---

### Post by mhenriday on 2009-07-27
**Varubhatbm**, from what you write I gather that you now see the **SCIM** icon on your system tray, so we seem to be making progress, albeit slowly....

Firstly, can you, just to get the matter out of the way, confirm that it is, indeed, **Firefox 3.5.2pre** that loads when you click your **FF** icon (click «Help» in the **FF** menu bar and select «About Shiretoko»)? When this is confirmed, the next step would be to follow the procedure for installing **SCIM** (I realise that you already have the programme installed, but my experience is that re-doing this procedure is sometimes necessary, and it certainly can't hurt) on this **Ubuntu** community documentation page (**_[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)_**). Don't forget the procedure under «In Case All of This Doesn't Work», if you don't get **SCIM** working previously and that you will have to re-boot to enable your changes....

Henri

---

### Post by Karnex420 on 2009-07-28
I'm in Shanghai and repository is no longer available here or I have network problems.
?

---

### Post by mhenriday on 2009-07-28
**Karnex420**, what do you see under the «Ubuntu software» tab when you do «System» &#8594; «Administration» &#8594; «Software Sources» ? If your query is not related to problems with **SCIM** after updating to **Firefox 3.5.x**, please start a new thread - we don't want to inadvertently kidnap **Varubhatbm**'s thread !...

Henri

---

### Post by Karnex420 on 2009-07-29
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/Ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/Ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found

?

---

### Post by mhenriday on 2009-07-29
**Karnex**, there were several orthographical errors in your URL. You might want to try clicking this [**_[COLOR="Blue"]*link*[/COLOR]_**]("http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/jaunty/main/binary-i386/") and then selecting «Packages». But as your query doesn't seem to be related to **varunbhatubm**'s problem with **SCIM**, it would be best if you were start a new thread in the event you wish to discuss this matter further....

Henri

---

### Post by Karnex420 on 2009-07-29
My SCIM icon disappeared.  I can't get SCIM to work.  And I can't get the pre-release of firefox 3.5.2.
Here is the last part when I update after following your instructions.
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/universe Sources     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
  404 Not Found
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/Ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/Ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

I think this is important for foreigners in China and I do appreciate your trouble but I also think I am on topic.

---

### Post by mhenriday on 2009-07-30
My apologies, **Karnex420** ! You hadn't mentioned not being able to get **SCIM** to work in your previous postings, which is how I gained the impression that you were off topic. Still, your main problem just now seems to be that you get an error message when you click «Packages» on the index page to which I provided a link above. I have no idea why this is the case, but «Packages» is just a text file showing all the included packages and thus wouldn't help you with the installation anyway. You could try clicking on either the **.bz2** or the **.gz** packages, downloading, and extracting the files, just to see if that is possible there in good old &#19978;&#28023;. However, given the fact that this is a **SCIM** thread, and I know from experience that most of our fellow users don't concern themselves with **SCIM**, it still might not be a bad idea to open a new thread with a title like «Problems downloading Ubuntu ppa files in China», which might attract more attention from fellow users who've encountered similar difficulties....

Henri

---

### Post by varunbhatbm on 2009-07-30
Thanks a lot Henri.
So far in ubuntu forum, no one has replied to my query with so much enthusiasm as you did.  :) 
SCIM is working properly now.. I followed the steps, given in Ubuntu SCIM URL you provided. It worked nicely :)

---

### Post by mhenriday on 2009-07-31
Wonderful to hear that **SCIM** is now working as it should on your system, **varunbhatubm** ! That's what these user fora are for - mutual aid (thanks, Prince Kropotkin) ! Now if **Karnex420** reports back on his experiences, preferably on a new-started thread, so that we can see why he is having difficulties downloading and installing the ppa packages....

Henri

---

