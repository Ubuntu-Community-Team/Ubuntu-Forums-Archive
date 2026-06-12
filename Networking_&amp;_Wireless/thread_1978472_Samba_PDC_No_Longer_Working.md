---
title: "Samba PDC No Longer Working"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by NickellossAych on 2012-05-11
I setup a Samba PDC for use with Windows XP Professional Clients. After initial setup, everything was working correctly. I could log on with each of the 5 users I created on two different computers, and files / folders were being synchronized correctly. The only issue was the desktop background would not save and a Desktop file in notepad would open. I ignored that issue.

Now the problem is that the clients cannot connect to the server any more. When I try to log on, I get 

```

Windows cannot locate the server copy of your roaming profile and is attempting to log you on with your local profile. Changes to the profile will not be copied to the server when you logoff. Possible causes of this error include network problems or insufficient security rights. If this problem persists, contact your network administrator.

```

Logon then continues to a local profile where I get the taskbar notification of "Offline Files - Working Offline" and the H: drive is not mapped.

I think the issue is somehow revolving around the fact that I shutdown the server last night, and then restarted it this morning.

Thinking the issue could be resolved by re-adding the computer to the domain, I attempted to do that and got 
```

A domain controller for the domain MY_DOMAIN could not be contacted.  The error code was: DNS name does not exist."

```

I don't know what the issue could be because like I said it was working fine earlier (except for the desktop issue). Today I added my W7 professional computer to the domain and logged on successfully - so now I am not sure if it's a server issue or a client issue.


Any help would be greatly appreciated.
If you ask for any type of error log, please specify how to obtain it as I am a novice at networking.

---

