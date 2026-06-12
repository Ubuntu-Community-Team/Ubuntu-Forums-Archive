---
title: "Network Manager Bug  in Jaunty - 9.04"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by measekite on 2009-06-12
Posted before under bad title.  Sorry

I and can get to the internet fine after some difficulty with using [COLOR=Navy]Network Manager (NM)[/COLOR].  For purposes here I named my connection **net1** and my ssid as **ssidnet.**

**Issue/Bug 1**
**Connect Automatically does not work.**
Upon reboot or a user logs off and a new user logs on the same machine the **[COLOR=RoyalBlue]net1[/COLOR]** does not connect automatically.  The user has to do it manually and that is a weird procedure described later in this post.

The box was checked "[COLOR=RoyalBlue]**Connect Automatically**[/COLOR]" but just does not work in this case.


**Issue/Bug 2**
**Available to All Users does not work**
Similar to Issue/Bug 1 when a new user is CREATED using Users and Groups there is no configured network icon. You have to create and configure it from scratch using **NM.**  Once you do that then you need to follow the connection procedure as previously described since [B]Connect Automatically does not work.
[/B]
To attempt to correct this I edited the connection using NM and checked "**Available to All Users**" near the bottom of the dialog box and when tried to apply it the **[COLOR=RoyalBlue]CONNECT[/COLOR]** button was **[COLOR=RoyalBlue]grayed[/COLOR]** out and I could not complete (OK button) the correction so I do not know if it is a mater of just unlocking the button or what.

For what ever it is work Fedora 11 uses what appears to be the same connection manager and has the same problems.

**Issue/Bug 3**
[COLOR=Red]Now for the real dumb thing. [/COLOR] 

Situation:
You reboot and the connection icon has an x like previous described and you are not connected. So you left click on the icon and you see a small dialog box and there is a filled in radio but next to your connection showing your network ssid1.

Now you would think you should have a connect button there or the actual name ssid1 should be a connection button itself but that would be too easy and sensible.

No you need to figure out this [COLOR=Red]**confusing choice**[/COLOR].  You have to choose "**Connect to Hidden Network**".  Why this says hidden network when you ssid is at the top with a checked radio button is beyond me but this is what there is.

After you choose "Connect to Hidden Network" you are presented with another dialog box with a combo box that says Create New Connection which of course you most likely will not want to do. You hit the drop down and there is your connection **net1.** You choose it and then press the connect button and you are connected to the net.  

I would very much appreciate any comments, workarounds, fixes, bug reports or any other information on all of these things and who else has experienced them with Jaunty 9.04. Feisty that I was using did not have these issues.

For What Ever It is Work I was seriously contemplating on moving to Fedora 11 but they had the same issues and other that were worse. I just got the feeling that Fedora is a very good Release Candidate for Red Hat like Open Suse is a Release Candidate for Novell. Still very good but I do not want to be a beta tester. Still I would like to have the leading technology but with the stability of Ubuntu.




**Issue 4**
Earlier releases has a signal strength bar for speed and strength of the wirles signal along with other information that was usefull and a green light when connected. This is now missing. You do have a few vertical bars on the icon when connected but it would be nice if it was green.


I would appreciate any comments, bug reports, work arounds who reports on who else has experience this. I was conteplating on moving to Fedora 11 but they have the same problems (probably in Network Manager) as Jaunty. Besides Fedora 11 seems like a good Release Candidate for Red Hat as Open Suse is for Novell and I just do not want to be a beta tester. Besides I had been using Feisty for a couple of years with very little problems.

I just would like to see the repositories get update with newer versions of applications when they come out and for Ubuntu releases to be supported for 27 months instead of 18.

Again thanks in advance.

---

