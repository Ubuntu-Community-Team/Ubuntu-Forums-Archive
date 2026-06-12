---
title: "I cannot access facebook or netflix from my linux computers"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by finer recliner on 2011-02-27
The problem started happening a few days ago. Only my linux computers are affected. Yup, that's right. My roommates running windows have zero problems.

What's the problem? Suddenly, I cannot access 2 websites: namely facebook and netflix. I just get a "waiting for facebook.com" status from my browser, and it waits there patiently until the browser finally gives up. I haven't found any other sites that give me this issue. Gmail, youtube, flickr, etc all work fine.

This happens using both firefox and chrome browsers. I've tried using Ubuntu 10.10 (on my desktop) and Peppermint (distro based on ubuntu, runs on my laptop). Both machines access the internet via wifi. Both have the same problem! o_O

Both machines are up-to-date. I've rebooted many times. I've tried booting an old kernel. I haven't installed any new software lately. I've tried disabling all plugins for the browsers. I've tried power-cycling our internet modem. I've tried changing my DNS settings to use [Google's Public DNS service]("http://code.google.com/speed/public-dns/"). Nothing helps.

Actually, one small piece of information: If I put my browser in incognito mode, I can get to the "sign-in" page for both facebook and netflix. But upon putting in my credentials, I still cannot reach my custom user home page for either site.

I've never seen a problem like this before. Have any of you?
Anyone have any ideas or suggestions? Any help at all would be greatly appreciated. Thank you.

---

### Post by luismendonca on 2011-05-05
I have basically the same problem here, but I'm using Ubuntu 11.04. All browsers (Firefox, Chromium, Opera) don't open pages like facebook.com, the same way you've described. Strangely, when I use incognito mode, I can get to the sign-in page, put my credentials and reach my custom user home page. But thereafter nothing works: I can't access the links, profiles (mine and of other people), not even page down the updates. Everything works well with Windows, installed on the same PC. I've realized that the internet speed in Ubuntu has been meaningly slower than in Windows. Anyone knows what's the matter, please?

---

### Post by dineshs on 2011-05-05
luismendonca,
You may try disabling [ipv6]("http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can?redirectlocale=en-US&redirectslug=Firefox+cannot+load+web+sites+but+other+programs+can")
Or Find an optimum value for [MTU]("http://ubuntuforums.org/showthread.php?t=872346")
BTW How do you connect to internet ethernet?Do you use DSL connection?

---

### Post by finer recliner on 2011-05-05
> **luismendonca said:**
> I have basically the same problem here, but I'm using Ubuntu 11.04. All browsers (Firefox, Chromium, Opera) don't open pages like facebook.com, the same way you've described. Strangely, when I use incognito mode, I can get to the sign-in page, put my credentials and reach my custom user home page. But thereafter nothing works: I can't access the links, profiles (mine and of other people), not even page down the updates. Everything works well with Windows, installed on the same PC. I've realized that the internet speed in Ubuntu has been meaningly slower than in Windows. Anyone knows what's the matter, please?

I was unable to find the cause for my original problem, but after a week or 2, it went away on it's own. I have a feeling that it was caused by my ISP (Verizon FIOS), but I have no evidence that it was definitely their fault. I'm sorry I can't offer more help. I know it's a strange and very frustrating issue :(

---

### Post by brott8 on 2011-05-30
I get the same issue.  This happens for youtube and facebook on Chromium and Firefox.  I am using Natty (11.04).

I tried disabling IPv6 following dineshs link and then rebooting the OS, but no change.  The websites seem to be accessible at random times, and then will stop responding after a few minutes of usage (especially facebook).  I have tried on both wireless and wired, and on multiple networks.  My ipad on the same connection does not suffer from the issue.

I can usually get to Facebook and Youtube via incognito mode (and can actually log in).  Facebook will usually stop responding after a couple minutes, and will function again if I close and re-open the incognito window.

This only began happening once Natty was installed.  I had no issues with previous versions of Ubuntu.  I may have to revert to 10.10 if I cannot resolve this.

Any ideas?

---

### Post by lanang23 on 2011-07-29
you should enable your modem firewall. i have same problemo and now it's fixed \\:D/

---

### Post by haqking on 2011-07-29
I had the FB problem a couple of days ago, i hadnt used FB for a while and only recenlty re-enabled it then couldnt access the page for like 2 days about 3 days after re-enabling.

I cleared the history completely and it worked fine.

---

### Post by Nasrid on 2011-08-03
Hi thank you for the incognito solution, actually I have exactly the same problem, could not access to facebook -am using Ubuntu 10.10 - the Maverick Meerkat- , using chrome under incognito has resolved the problem, but still is not great as it is hard to see my Messages and to post a link- it takes unlimited time...but I can go to my wall and others wall, let see if I can discover why is still bad, 

Regards,

---

### Post by Nasrid on 2011-08-06
well, I was very wrong, it did not solve anything as I could acces on facebook only the first time that I  used incognito mode then no more, i can see only the the bleu panel, the same issue with monster i cannot go on the login page and other web site like companies, so is it a probleme with my dns ? i have added to servername that i found on another forum solution and it did not help, i have installed sun java plugin (allows to run some application on web browser) it did nothing, if i can see the bleu panel does it mean that the facebook server has recieved my request and that is trying to reply so if i do not have reply does it mean that the server name that my internet network is using does not know facebook ? well very wierd , please help particularly for monster.com and theother web site as am looking for a job.

and tried both with chrome and firefox, 
 
Thank's

---

### Post by anuragchauhan00 on 2011-09-18
any solutions for this yet ? 
I am having the exact issues as faced by you all.

---

### Post by haqking on 2011-09-18
> **anuragchauhan00 said:**
> any solutions for this yet ? 
I am having the exact issues as faced by you all.

Netflix do not support Linux

As for facebook, you might need to enable allowingit for NoScript or Adblock, also if you have security i think Facebook requires you allow cookies.

I dont use FB anymore so cant remember.

Do you have Noscript or Adblock running ?

---

### Post by diegoguimaraes on 2012-05-09
I had the same problem, and after making a lot of research on the internet, I remebered that I restarted the router matching with beginign of this problem. So, in this case the MTU was set back to default value 1500.
I solved it in the following way:

On the router admin page I set the MTU value to 1402 and the DNS primary to 8.8.8.8 and the secondary to 8.8.4.4

My net is DSL, System Ubuntu 12.04.

I hope this help.

---

