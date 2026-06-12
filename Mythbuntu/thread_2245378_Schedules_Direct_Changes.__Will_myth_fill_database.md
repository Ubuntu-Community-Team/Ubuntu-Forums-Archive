---
title: "Schedules Direct Changes.  Will myth fill database stop working Nov 1st?"
date: 2014-09-23
forum: Mythbuntu
---

### Post by topcat5 on 2014-09-23
Please reference [this announcement]("http://forums.schedulesdirect.org/viewtopic.php?f=7&t=2577") from the Schedules Direct site.  Obviously for anyone that relies on mythfilldatabase and SD for scheduling purposes, this means a big problem.  I guess this is mostly North American users.  

It's mentioned in the topic that a grabber has already been developed (in beta?) that will be the replacement, but it's not compatible with the current system.  Is there any work or plans to make this available through a mythbuntu upgrade?  Or should we go ahead and try to figure it out on our own.   Thanks.

---

### Post by tgm4883 on 2014-09-23
> **topcat5 said:**
> Please reference [this announcement]("http://forums.schedulesdirect.org/viewtopic.php?f=7&t=2577") from the Schedules Direct site.  Obviously for anyone that relies on mythfilldatabase and SD for scheduling purposes, this means a big problem.  I guess this is mostly North American users.  

It's mentioned in the topic that a grabber has already been developed (in beta?) that will be the replacement, but it's not compatible with the current system.  Is there any work or plans to make this available through a mythbuntu upgrade?  Or should we go ahead and try to figure it out on our own.   Thanks.   


(Please forgive if there is already a topic about this.  I didn't see one.)

If the local IP address and the master IP address are not the same in mythtv-setup then it thinks it's a slave backend. How are you running mythtv-setup?

---

### Post by topcat5 on 2014-09-24
> **tgm4883 said:**
> If the local IP address and the master IP address are not the same in mythtv-setup then it thinks it's a slave backend. How are you running mythtv-setup?

I don't understand this question in the context of this post.  It seems to have nothing to do with the subject.

---

### Post by RichardK3 on 2014-09-24
> **topcat5 said:**
> Please reference [this announcement]("http://forums.schedulesdirect.org/viewtopic.php?f=7&t=2577") from the Schedules Direct site.  Obviously for anyone that relies on mythfilldatabase and SD for scheduling purposes, this means a big problem.  I guess this is mostly North American users.  

It's mentioned in the topic that a grabber has already been developed (in beta?) that will be the replacement, but it's not compatible with the current system.  Is there any work or plans to make this available through a mythbuntu upgrade?  Or should we go ahead and try to figure it out on our own.   Thanks.   


(Please forgive if there is already a topic about this.  I didn't see one.)

There is an extensive discussion going on here:

[http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=575818;page=1;sb=post_latest_reply;so=ASC;mh=25;list=mythtv](http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=575818;page=1;sb=post_latest_reply;so=ASC;mh=25;list=mythtv)


Details are still being worked out, but it sounds like there will be a relatively seamless transition for users of MythTV 0.27.   For those who haven't upgraded, the situation is less clear.

---

### Post by topcat5 on 2014-09-24
> **RichardK3 said:**
> .....

Details are still being worked out, but it sounds like there will be a relatively seamless transition for users of MythTV 0.27.   For those who haven't upgraded, the situation is less clear.

Thanks for the info. It was rather alarming when I saw it on the SD site when I went to update my lineup.   I'm glad upgraded my entire system to 0.27 about a month ago.

---

### Post by tgm4883 on 2014-09-24
> **topcat5 said:**
> I don't understand this question in the context of this post.  It seems to have nothing to do with the subject.

I.. I'm not even sure how that ended up in this thread. I was pretty tired yesterday, so I'm going to blame it on that.

---

### Post by itlarson2 on 2014-09-24
Glad I logged in and saw this!  Could someone smarter than me write up a how-to for migrating to the new system?

---

### Post by tgm4883 on 2014-09-25
> **itlarson2 said:**
> Glad I logged in and saw this!  Could someone smarter than me write up a how-to for migrating to the new system?

The topic is actually 100% completely false, as SD support is not ending and the post title suggests that guide data in the US will need to come from somewhere else. I urge OP to change the title if they can, but won't blame OP though because if you read the post this is a bit confusing without context

> We have been informed that Gracenote (formerly Tribune Media Services) will be ending the guide data service currently used by most users of Schedules Direct. Their plan is to end support for this service on November 1, 2014.

After discussing this with upstream MythTV what this means is that Gracenote is stopping the XML based service that Schedules Direct is passing on to us (which is also what mythfilldatabase uses in the US). This is getting replaced by a more modern JSON based service. Now that would mean that MythTV would need to be updated so mythfilldatabase could use the newer JSON service. However, that post also reads

> In addition to the JSON service, a separate service is being developed to mimic the DataDirect feed. It's not ready yet but should be able to provide basic functionality for those legacy applications that can't move to JSON. It is expected to have most, but not all of the data currently in the Data Direct feed and will be updated daily. More details will be available about this later.

What probably will happen is that 0.28 will roll out with the new JSON grabber stuff via XMLTV, and we'll need a nice way to configure the XMLTV stuff with our SD credentials. I would expect 0.27 to function as before, perhaps with slightly less detail in the guide data.

---

### Post by topcat5 on 2014-09-26
> **tgm4883 said:**
> The topic is actually 100% completely false, as SD support is not ending and the post title suggests that guide data in the US will need to come from somewhere else. I urge OP to change the title if they can, but won't blame OP though because if you read the post this is a bit confusing without context.There is nothing false about what I've posted and I don't see how anyone could be confused.   I was careful to place a link to the actual announcement directly in the post.  Furthermore, a link to the discussion as to what will happen (from a mythtv perspective) is posted in this topic as well.  Schedules Direct support for the existing guida data via mythfilldatabase ends on November 1.   

Furthermore, I find your post confusing & misleading because you suggest something that might or might not happen but you give no official announcement or source for that information.  This change is happening in just a few weeks so IMO, the unnecessary noise & drama should be kept to a minimum.  

From the perspective of existing Mythbuntu users, it's still not clear to me what existing Mythbuntu users should do, if anything.   November 1 isn't that far away.

---

### Post by tgm4883 on 2014-09-26
> **topcat5 said:**
> There is nothing false about what I've posted and I don't see how anyone could be confused.   I was careful to place a link to the actual announcement directly in the post.  Furthermore, a link to the discussion as to what will happen (from a mythtv perspective) is posted in this topic as well.  Schedules Direct support for the existing guida data via mythfilldatabase ends on November 1.   


The title of the post says that that Schedules Direct is ending support, indicating that US/Canada users will need to get their tv guide data from some source other than Schedules Direct post November 1st. This is not the case, Schedules Direct will continue to provide guide data. The service that provides guide data to Schedules Direct is changing, ideally this would have little to no impact on users. Sure you posted the link to the SD thread, but how many people click though to read that (and those that do, how many dig in and understand it) rather than just trust your title because "Hey, he sourced it so he knows what he is talking about". The post that you linked to is titled "TMS dropping Data Direct!!! But no reason to panic.", I'm not sure where you got the idea that Schedules Direct is ending support or why you thought to title your post that way. It's not close to what the topic you linked to was about.

> **topcat5 said:**
> 
Furthermore, I find your post confusing & misleading because you suggest something that might or might not happen but you give no official announcement or source for that information.  This change is happening in just a few weeks so IMO, the unnecessary noise & drama should be kept to a minimum.  


You are correct, I did not source any of my statements regarding "a separate service is being developed to mimic the DataDirect feed". I assumed that you knew where it from from, but apparently you fell into the category of people that I previously mentioned above "how many people click though to read that (and those that do, how many dig in and understand it)". The source for the statement of the "a separate service is being developed to mimic the DataDirect feed" was from the [first post in the Schedules Direct thread you linked to by remeden]("http://forums.schedulesdirect.org/viewtopic.php?f=7&t=2577&sid=780a9efc7d519487544c5a0667ece104#p7700"). 

> **topcat5 said:**
> 
From the perspective of existing Mythbuntu users, it's still not clear to me what existing Mythbuntu users should do, if anything.   November 1 isn't that far away.

November 1st is over 4 weeks away, and almost 2 months away from the original post on the SD forums. There is no news on what Mythbuntu users should do because either A) There is nothing that Mythbuntu users need to do or B) There isn't a clear set of steps for Mythbuntu users yet. 


I'm sorry if this came off a bit harsh, but one of my biggest pet peeves is posts/statements made that don't have all the facts that could be construed as FUD/Fear-mongering.

---

### Post by topcat5 on 2014-09-27
> **tgm4883 said:**
> 

I'm sorry if this came off a bit harsh, but one of my biggest pet peeves is posts/statements made that don't have all the facts that could be construed as FUD/Fear-mongering.And mine are people who respond with line by line rebuttals (which I don't read), and who add a lot of unnecessary noise to a topic.  Best avoided since you can always send a PM instead of hyperventilating about your pet peeves as you did in my topic.

This issue, Schedules Direct ending support for the current scheduling, is an important issue IMO, and we need to focus on the change.

I'd still like to hear how this change affects users from the perspective of using Mythbuntu.

---

### Post by RichardK3 on 2014-10-01
Apparently a direct replacement is now being beta tested.  If you'd like to help, all it requires is a one-line change to your hosts file.

[URL="http://forums.schedulesdirect.org/viewtopic.php?f=8&t=2591"]http://forums.schedulesdirect.org/viewtopic.php?f=8&t=2591
[/URL]
Just passing this along to anyone who might like to try it.

---

### Post by garsh on 2014-10-03
I see that I currently only have 7 days of guide data, even though I just ran mythfilldatabase.
Is this somehow related to this announcement?
Is anybody else seeing this?

---

### Post by tgm4883 on 2014-10-03
> **garsh said:**
> I see that I currently only have 7 days of guide data, even though I just ran mythfilldatabase.
Is this somehow related to this announcement?
Is anybody else seeing this?

That sounds unrelated since nothing has happened yet. I would open a new thread explaining the issue with logs

---

### Post by tgm4883 on 2014-10-04
It's looking like this is going to need a code change in the backend and that the easy DNS change isn't going to be made.

---

### Post by tgm4883 on 2014-10-04
I've uploaded packages with the DNS change here [https://launchpad.net/~mythbuntu-bugs/+archive/ubuntu/test1/+packages](https://launchpad.net/~mythbuntu-bugs/+archive/ubuntu/test1/+packages)  If you test them, please report back

---

### Post by tgm4883 on 2014-10-09
> **tgm4883 said:**
> I've uploaded packages with the DNS change here [https://launchpad.net/~mythbuntu-bugs/+archive/ubuntu/test1/+packages](https://launchpad.net/~mythbuntu-bugs/+archive/ubuntu/test1/+packages)  If you test them, please report back

I've heard nothing back on the testing of the proposed fix. You can test it pretty easily with the instructions here  [https://sites.google.com/a/mythbuntu.org/website/testingandreporting#TOC-Testing-Bug-Fixes](https://sites.google.com/a/mythbuntu.org/website/testingandreporting#TOC-Testing-Bug-Fixes)

The proposed fixes are available here [https://launchpad.net/~mythbuntu-bugs/+archive/ubuntu/test1](https://launchpad.net/~mythbuntu-bugs/+archive/ubuntu/test1) 

Please report results back to this thread.

---

### Post by topcat5 on 2014-10-12
As the OP, maybe it would be better to close this topic and start another one which details what is suppose to happen over the next two weeks.   This topic has served its purpose.   

There seem to be two approaches.

[LIST=1]
[*]The external Json grabber developed by SD
[*]The DD replacement that seems to only require a DNS change. 
[/LIST]

I'm still confused as to which is the better approach.   

What I would hope to see would be some sort of recommendation for users of the current version of Mythbuntu as to the approach that should be used so we can start getting ready for it.   

Thanks.

---

### Post by tgm4883 on 2014-10-12
> **topcat5 said:**
> As the OP, maybe it would be better to close this topic and start another one which details what is suppose to happen over the next two weeks.   This topic has served its purpose.   

There seem to be two approaches.

[LIST=1]
[*]The external Json grabber developed by SD
[*]The DD replacement that seems to only require a DNS change. 
[/LIST]

I'm still confused as to which is the better approach.   

What I would hope to see would be some sort of recommendation for users of the current version of Mythbuntu as to the approach that should be used so we can start getting ready for it.   

Thanks.

I'm still not 100% sure what the topic of this post was for, that said, users will need to grab an update from the mythtv updates repo (for any supported mythtv version eg. 0.27) provided by the Mythbuntu team. The Update repo is the recommended way to get updates.

---

### Post by topcat5 on 2014-10-13
OK, so it sounds as if the JSON grabber isn't part of the MythTV/Mythbuntu roadmap.  Scratch that option?    

This wiki link is the preferred alternative which will be provided by the Mythbuntu team when MythTV makes it available?   (presumably before Nov 1)

[http://www.mythtv.org/wiki/Schedules_Direct_Replacement_Service]("http://www.mythtv.org/wiki/Schedules_Direct_Replacement_Service")


(I'm not trying to be obtuse.  I'm just trying to avoid picking the "non-preferred" approach to fixing this issue.)

---

### Post by tgm4883 on 2014-10-13
> **topcat5 said:**
> OK, so it sounds as if the JSON grabber isn't part of the MythTV/Mythbuntu roadmap.  Scratch that option?    


For 0.27, no. For 0.28, it may be recommended to change to that.

> **topcat5 said:**
> 
This wiki link is the preferred alternative which will be provided by the Mythbuntu team when MythTV makes it available?   (presumably before Nov 1)

[http://www.mythtv.org/wiki/Schedules_Direct_Replacement_Service]("http://www.mythtv.org/wiki/Schedules_Direct_Replacement_Service")


(I'm not trying to be obtuse.  I'm just trying to avoid picking the "non-preferred" approach to fixing this issue.)

Correct. It's actually already available for testing in the PPA I mentioned in an earlier post, and also available for testing in 0.28. The preferred approach would depend on the MythTV version you are running.

If you are running 0.28, then upgrade to the Oct 13th or later packages and you will be using the DD replacement service. Currently this is the recommended solution but may change as 0.28 develops (as it's still in development)
If you are running 0.27, then upgrade to the packages that contain the fix once it's released
If you are running something other than those, either A) Upgrade to 0.27 and to the fixes repo that contains the fix. or B) Set up either the hosts file additions or a local DNS server to point to the correct URL

---

### Post by tgm4883 on 2014-10-15
[http://www.mythbuntu.org/home/news/actionsrequiredbynov1stduetoschedulesdirectchange](http://www.mythbuntu.org/home/news/actionsrequiredbynov1stduetoschedulesdirectchange)

---

### Post by Elfy on 2014-10-15
> **tgm4883 said:**
> [http://www.mythbuntu.org/home/news/actionsrequiredbynov1stduetoschedulesdirectchange](http://www.mythbuntu.org/home/news/actionsrequiredbynov1stduetoschedulesdirectchange)

Do you want that copied to a thread and stuck in here for a while?

---

### Post by larsolav on 2014-10-15
> **tgm4883 said:**
> [http://www.mythbuntu.org/home/news/actionsrequiredbynov1stduetoschedulesdirectchange](http://www.mythbuntu.org/home/news/actionsrequiredbynov1stduetoschedulesdirectchange)

Well, that was easy!!

---

### Post by tgm4883 on 2014-10-15
> **Elfy said:**
> Do you want that copied to a thread and stuck in here for a while?

Thanks Elfy, but I don't think so. If I start seeing a bunch of theads pop up on this then maybe we should, but it's such a painless fix that we recommend people be on our update repo anyway that I'm not sure if it's necessary. On second thought, maybe we should for those users that aren't on the service. Let me create a new post and I'll ping you to sticky it.

> **larsolav said:**
> Well, that was easy!!

I told you guys you were making a bigger deal out of it than it actually was ;)

---

### Post by topcat5 on 2014-10-16
> **tgm4883 said:**
> 


I told you guys you were making a bigger deal out of it than it actually was ;)It has been clearly explained on the MythTV homepage (See Oct 15) including the status of the JSON grabber.  (i.e.  Don't use it)   I agree with them on the "unfortunate" moniker.    I've updated and it seems to work fine.   

I'm glad it's been cleared up.  

[http://www.mythtv.org/]("http://www.mythtv.org/")

---

