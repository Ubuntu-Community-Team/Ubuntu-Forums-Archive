---
title: "Cannot surf with firefox all the sudden.."
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by DJYoshaBYD on 2010-06-25
ok.. so first off, im a networking professional, and my network will surf fine.. I can use any other computer on my network for surfing, and its fine..

The problem im having is firefox on my server.. I use it for browsing when im in a blocked network, such as work..

Now, this SAME server works fine, if i surf using Lynx (command line browser), but if I use firefox, it gets halfway through loading a page, and just sits there.. it takes a long time to even time out..

now, it was fine before, and im pretty sure this is some sort of firewall i accidentally installed, but I dont know how to check, as i have only been using linux for 2 years...

i have completely uninstalled firefox, and reinstalled it, as well..

specs are as follows

intel p4 3.2 HT
1gb ddr2 800
1tb HD
Ubuntu 8.04 LTS, fully updated, 32 bit..

anything i should check?

and yes.. i have power cycled the router, etc etc etc.. its NOT my network, its SPECIFICALLY firefox on my server..

thanks 

:popcorn:

---

### Post by jonobr on 2010-06-25
Hello

somethings are stored in your profile and are not removed by removing and reinstalling.
Some config files etc can still linger round.

Did you remove those after reinstalling?

It also sounds like as if you watched for plugins addons and themes, so I assume they arent the issue.

Did you remove the [Installation directory]("http://kb.mozillazine.org/Installation_directory")after removing ff?

You sound like a savvy person so Id say my comments are useless

---

### Post by DJYoshaBYD on 2010-06-26
NO.. hahaha. not at all.. ANY comments will help.. i didnt even think to do that..lol.. ****..i have posted on here a few times and got ZERO responses, or responses from people that didnt read the post, and ask something that was already covered.. haha.. you are alllllllll good :)

another thing.. Ill close firefox, try to reopen, and it says its still running.. no matter what, when i close it, it keeps the process running... this is for sure pointing..

im going to try and troubleshoot this tomorrow at work (we are dead on sats).. im going to remove it, and delete all associated folders to see if that helps..

any other suggestions would work, as well..
:guitar:

---

### Post by DJYoshaBYD on 2010-06-26
well, apparently, you are genius.. lol.. deleting all that crap fixed it up...

thanks for that :)

we will see how it works tomorrow

sorry for not checking that first.. Im running a pretty advanced linux server, but hell.. im still learning.. lol

thanks..

Josh
opensource Biaaaaaaaaaatttttccccccccchhhhhhhh

---

### Post by jonobr on 2010-06-26
Glad to hear its working and , arent we all learning!

---

