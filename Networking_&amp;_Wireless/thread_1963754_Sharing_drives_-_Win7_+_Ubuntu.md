---
title: "Sharing drives - Win7 + Ubuntu"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by Metal Mick on 2012-04-22
I have 3 PCs: one with Win 7 64-bit; one with Win 7 32-bit; my laptop with Ubuntu 11.

I am trying to file share across a home network (on both Win machines drive D) for the Ubuntu machine – the two Win machines share without issue.

So far, I've had no success, despite Ubuntu machine being able to see the C:\Users\Public folder, the files, and being able to open and write to that directory on both Win machines.

When I try to mount the D drive, I get the much-hated “Unable to mount... Failed to mount Windows Share” message. Despite this, if I set a directory – on D or elsewhere – to sharing, it is detected by Ubuntu machine promptly.

I have followed Ben Page's instructions in this thread, because the OP's experiences are similar to mine:

[http://ubuntuforums.org/showthread.php?t=1702699](http://ubuntuforums.org/showthread.php?t=1702699) 

- to no avail.

Obviously, I have Samba installed and working on Ubuntu machine. I can't help but feel though, that it is Win7 that is stopping things from progressing, but checking the sharing settings for the various drives and folders on Win7 has so far not shown any difference. I've had no issues with sharing, with the same hardware and WinXP.

I've Googled, and searched here for help, and found that the suggestions are very similar even to the extent of them not working for me. Any further help is very much appreciated.

Michael P

---

### Post by Metal Mick on 2012-04-23
Hi all,

much to my surprise, I have been able to make progress with this.

I have found for both my machines that to some degree, the instructions I quoted above, were correct though perhaps needing a little more information.

I've found that by following the instructions, and ensuring I include "Everyone" as someone who gets access, I can reliably mount ***folders ***but* not * entire drives.

This is satisfactory to me, but I can live with it. I'll leave this thread open - as opposed to tagging it "Solved" - for now just in case someone has found a way of mounting entire drives.

I hope this has helped, and thanks to all who have helped me in the past.

Regards,

Michael P

---

### Post by dandnsmith on 2012-04-23
I haven't checked the instructions you linked to, but offer a couple of comments (in case it helps)

I've a small home network, with PCs running WinXP, Win7 and Ubuntu/Mint (several flavours). I have it set to share partitions ( which Windows insists on referring to as 'drives') on all the machines.
I only have read permissions set, as a matter of principle, so always have to pull info, not push it.

I don't use HomeGroup in the Win7 PC - a real NONO!

I haven't put any effort into sharing external drives, as the volatility renders this a bit more of an effort.

I don't use the *mount* command - it all gets done by file explorer reference (all machines).

---

### Post by Metal Mick on 2012-04-24
> **dandnsmith said:**
> <snip>

I've a small home network, with PCs running WinXP, Win7 and Ubuntu/Mint (several flavours). I have it set to share partitions ( which Windows insists on referring to as 'drives') on all the machines.
I only have read permissions set, as a matter of principle, so always have to pull info, not push it.

I don't use HomeGroup in the Win7 PC - a real NONO!

I haven't put any effort into sharing external drives, as the volatility renders this a bit more of an effort.

I don't use the *mount* command - it all gets done by file explorer reference (all machines).

Many thanks Derek,

but I prefer read/write status.

How do you get around not using Homegroup; "sharing partitions" - doesn't Windows see these as discrete drives; and I don't understand how you've bypassed the mounting of drives?

would you be able to enlighten me somewhat?

Cheers,

Michael P

---

### Post by dandnsmith on 2012-04-24
I feel a bit wary about posting Windows stuff on such a forum, as I'm sure some will disapprove but -

HomeGroups are an aberration introduce by M'soft for W7 - they don't even work with any earlier version of Windows!
If you go to Control Panel and look for the Internet and Sharing stuff, you can set to use a work group (which is closer to the older windows way of doing things, and can coexist with WinXP and linux). There is a whole screenful of options, where you can choose the best for you (I don't have either the Win7 to hand or the thread where I spelled this out a few days ago (may be in other forums completely, not ubuntu).

Yes, Windows lists partitions as drives, confusing it with other physical drives, and totally different from the monolithic linux filesystem. When sharing is carried out successfully, neither Windows nor linux need to have drives/partitions explicitly mounted by the user. All the mounting, in the case of linux for remote sharing, can be addressed through use of the file explorer, which will cause automatic mounting of a share. Windows behaves similarly.

There may be a matter of providing passwords to verify access authority - but both OS types have ways of rendering this automatic once the mechanism has been primed.

I hope that helps somewhat - are there bits which I haven't adequately described?

---

### Post by Morbius1 on 2012-04-24
Windows never has liked it's users to share entire drives. In the past when you attempted to try it a dialog box would pop up and ask you are you sure or something like that. In Win7 it's become formalized.

I just did this on Win7 and successfully accessed the share from Ubuntu. On WIn7: Right Click the Drive > Properties > Sharing > Advanced Sharing > check "Share this Drive". 

I have no issues acessing this share from Linux despite the fact that I have HomeGroup enabled and the Win7 machine and the Ubuntu machine are in 2 different workgroups. 

Now I do things a little different with Win7 since it's sharing methodology is more like Win2000 than WinXP. Windows has real problems with the concept of "guests" and "Anonymous Logins" and "Everyone" is a misnomer. It's not everyone on the network it's every local Win7 user so I gave in to the dark side and did things the Win7 way since long periods of use in Win7 gives me the willies: 

** Instead of a true guest share I created a user on Win7 called samba and gave him a sambapw password.
** Then I allow "Everyone" to access the share under Permissions .

When you try to access the share from Linux you will get a prompt at the Hostname level - use samba. You'll get another prompt at the share level - use samba. If it all works you can have Ubuntu remember all these credentials "forever" so it becomes seamless.

---

### Post by Metal Mick on 2012-04-24
> **dandnsmith said:**
> <snip>
If you go to Control Panel and look for the Internet and Sharing stuff, you can set to use a work group (which is closer to the older windows way of doing things, and can coexist with WinXP and linux).<snip>

I hope that helps somewhat - are there bits which I haven't adequately described?

Many thanks Derek for taking the time to go further on this.

Firstly, under Internet and Sharing, I don't have any option to change or create a Workgroup - so I believe you are referring to setting the network to "Work".

Digging deeper - Microsoft has thoughtfully scattered information around for us, giving many the opportunity to curse and rip out hair in frustration - I have found that my Win machine is a part of "WORKGROUP", so I appear to have done something right.

I shall persist with this - I would like to have the "drives" mounted purely for ease of use although I can live with just folders.

I'll have another play and see what I can manage.

Cheers,

Michael P

---

### Post by Metal Mick on 2012-04-24
> **Morbius1 said:**
> Windows never has liked it's users to share entire drives. In the past when you attempted to try it a dialog box would pop up and ask you are you sure or something like that. In Win7 it's become formalized.

I just did this on Win7 and successfully accessed the share from Ubuntu. On WIn7: Right Click the Drive > Properties > Sharing > Advanced Sharing > check "Share this Drive". 

I have no issues acessing this share from Linux despite the fact that I have HomeGroup enabled and the Win7 machine and the Ubuntu machine are in 2 different workgroups. 

Now I do things a little different with Win7 since it's sharing methodology is more like Win2000 than WinXP. Windows has real problems with the concept of "guests" and "Anonymous Logins" and "Everyone" is a misnomer. It's not everyone on the network it's every local Win7 user so I gave in to the dark side and did things the Win7 way since long periods of use in Win7 gives me the willies: 

** Instead of a true guest share I created a user on Win7 called samba and gave him a sambapw password.
** Then I allow "Everyone" to access the share under Permissions .

When you try to access the share from Linux you will get a prompt at the Hostname level - use samba. You'll get another prompt at the share level - use samba. If it all works you can have Ubuntu remember all these credentials "forever" so it becomes seamless.

Thanks for the info Morbius1, but I - like many, many others - have tried the method you described to access a drive (in my case, dozens of times) and it has* never *worked, so some other issue must need to be resolved. The fact that the context (right-click) menu has different options for drives, and folders on that drive supports a premise that Win7 treats the two differently.

I was very surprised to read that it worked so simply for you - perhaps it is in how your workgroups are set up? You mentioned that you have two.

Creating a second user for each machine to permit sharing seems a bit strange - is it a workaround for some known bug in Win7? If so, I'm happy to try it.

Perhaps a good way to go is to turn off Homegroups and Workgroups, and sharing and then start the process again, this time avoiding Homegroups, since it appears to be somewhat problematic.

Many thanks again,

Michael P

---

### Post by Morbius1 on 2012-04-25
> I was very surprised to read that it worked so simply for you - perhaps  it is in how your workgroups are set up? You mentioned that you have  two.If all of your machines are connected to the same router workgroup names don't matter. Have as many as you want. From a Linux client perspective it's messier to do it that way since when you browse you'll have to drill down many workgroups to find the host. But when you browse in Win7 it doesn't list a workgroup name so the Windows user doeasn't even know there are multiple workgroups.
> Creating a second user for each machine to permit sharing seems a bit  strange - is it a workaround for some known bug in Win7? If so, I'm  happy to try it.That's not what I wrote. I was referring to having a true guest share where anyone can access the share anonymously . WinXP could create one, WIn7 not so much. 
> Perhaps a good way to go is to turn off Homegroups and Workgroups, and  sharing and then start the process again, this time avoiding Homegroups,  since it appears to be somewhat problematic.
I did not disable HomeGroups as it has no impact on me accessing the share but if it works for you .....

[COLOR=Blue]**EDIT: **[/COLOR]
You know something just occurred to me - it had to happen one day - it has to do the permissions on the "D Drive" itself. When you created the share using "Advanced Sharing" > "Permissions" you probably added or maybe it defaulted to "Everyone".

Did you do the same thing to the NTFS permissions? Properties > Security

You should have the group: Users (HOST\Users) listed. Does it allows Users to gain access to the drive itself? Worst case add "Everyone"

---

### Post by Metal Mick on 2012-04-25
> **Morbius1 said:**
> <snip>

[COLOR=Blue]**EDIT: **[/COLOR]
You know something just occurred to me - it had to happen one day - it has to do the permissions on the "D Drive" itself. When you created the share using "Advanced Sharing" > "Permissions" you probably added or maybe it defaulted to "Everyone".

Did you do the same thing to the NTFS permissions? Properties > Security

You should have the group: Users (HOST\Users) listed. Does it allows Users to gain access to the drive itself? Worst case add "Everyone"

As far as "something occurring to you..." don't sell yourself short - you've been a great help in the past (I recall your distinctive ID) and your suggestion re security has apparently done the trick.

I was wondering if the security tab might be the key, but hadn't gotten around to fiddling with it.

After a good fiddle, I can mount the drive, and navigate to wherever I wish on it. I have been unable to write to it, but seems just a matter of setting permissions.

Thanks again to everyone for their generous help.

Michael P

---

