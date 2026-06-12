---
title: "Trouble getting silverlight working with pipeline on chrome or firefox"
date: 2013-11-09
forum: Multimedia Software
---

### Post by hughreid01 on 2013-11-09
Hi, maybe someone can help me....
I cannot watch any of the 'catch-up' channels that use 'silverlight' and have been running through a few 'instructionals' to get it running through firefox or chrome.
I am using Xubuntu 13.04.

After a few hours with firefox i have got to the point where, according to the pipelight diagnostics website ([http://fds-team.de/pipelight/](http://fds-team.de/pipelight/))...

**User agent (Javascript)**
Checking for Windows user agent ...[COLOR=red]failed[/COLOR]
[COLOR=grey]Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:24.0) Gecko/20100101 Firefox/24.0[/COLOR]

**Silverlight (as seen by a website)**
Checking for Silverlight ...[COLOR=green]okay[/COLOR]
[COLOR=grey]Version: 5.1.20513.0[/COLOR]

**Result**
Result from all tests ...[COLOR=red]failed[/COLOR]
[COLOR=grey]You need to fix your user agent by installing a user agent switcher[/COLOR]

none of the user agent fields supplied on the website work ([https://answers.launchpad.net/pipelight/+faq/2351](https://answers.launchpad.net/pipelight/+faq/2351))

so i gave up and tried google chrome where i found a user agent that works but it tells me silverlight and pipelight are not installed.......

[COLOR=#000000][FONT=Times New Roman]**User agent (Javascript)**[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Checking for Windows user agent ...[/FONT][/COLOR][COLOR=green][FONT=Times New Roman]okay[/FONT][/COLOR]
[COLOR=grey][FONT=Times New Roman]Mozilla/5.0 (Windows NT 6.1; WOW64; rv:15.0) Gecko/20120427 Firefox/15.0a1[/FONT][/COLOR]
[COLOR=grey][FONT=Times New Roman]Please note: not every user agent works on every site, try multiple ones if something doesn't work![/FONT][/COLOR]

[COLOR=#000000][FONT=Times New Roman]**Silverlight (as seen by a website)**[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Checking for Silverlight ...[/FONT][/COLOR][COLOR=red][FONT=Times New Roman]failed[/FONT][/COLOR]

[COLOR=#000000][FONT=Times New Roman]**Pipelight**[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Checking for Pipelight ...[/FONT][/COLOR][COLOR=red][FONT=Times New Roman]failed[/FONT][/COLOR]
[COLOR=grey][FONT=Times New Roman]Do you have Pipelight installed and enabled systemwide?[/FONT][/COLOR]

[COLOR=#000000][FONT=Times New Roman]**Result**[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Result from all tests ...[/FONT][/COLOR][COLOR=red][FONT=Times New Roman]failed[/FONT][/COLOR]
[COLOR=grey][FONT=Times New Roman]Something is wrong with your pipelight installation

[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]And In terminal......
hugh@hugh-GA-MA78GM-S2H:~$ sudo pipelight-plugin --enable silverlight
Plugin silverlight5.1 is now enabled
[/FONT][/COLOR][COLOR=grey][FONT=Times New Roman]
[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]So firefox has silverlight installed but i cannot install it on chrome, must be time for break[/FONT][/COLOR][COLOR=grey][FONT=Times New Roman]........
[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]
I've gone through the pipeline installation again but no joy,
So, Can anyone please tell me how to get chrome to recognise pipelight and silverlight so i can watch big bang theory before it gets removed?[/FONT][/COLOR][COLOR=grey][FONT=Times New Roman]
[/FONT][/COLOR]

---

