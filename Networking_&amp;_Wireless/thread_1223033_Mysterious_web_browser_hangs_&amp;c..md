---
title: "Mysterious web browser hangs &amp;c."
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by Sean Whitton on 2009-07-25
Greetings,

I would like to try to report a problem I have been having with Ubuntu for a long, long time, that I have no real idea how to troubleshoot, and that (usually) doesn't occur when I boot to Windows (or on other Windows PCs on my home network). I have little to offer except the symptoms and some minor observations I've made. I'm at a total loss and while I continue to use Ubuntu it makes the experience pointedly less pleasant.

=== Main web browsing issue ===

My primary problem is, in short, my inability to HTTP POST data onto websites. This means that I can't fill in forms, upload files or even sometimes login (though that often works). As a Wikipedian this is a serious impairment! When I try to post a form, it hangs for ages, but not with Firefox telling me "Sending request to ..." but instead with "Waiting for ...", and then Firefox will offer me the PHP page or whatever for download, which makes no sense as the form data never actually gets there (I test this by viewing, say, a saved wiki page, and it doesn't save). Another example is my Internet banking, which has several login steps before displaying a summary of my accounts. While I can submit the form for each step fine, the summary page only occasionally manages to load completely.

AJAX-based and similar technologies are even more temperamental. Google's Gmail works flawlessly, but I cannot submit tweets to Twitter. All of these problems, except submitting proper forms, have exceptions where things work, but these are rare.

I've had to boot into Windows to make this post :-)

Crucially, this problem did not occur at a recent LAN party, suggesting there is nothing wrong locally and that it is my router that is at fault.

=== SCP oddness ===

I often need to SCP small files to my VPS but I find that unless they are very small the process mysteriously stalls. For example, the other day I tried to send a file of a few MB in size up, and the progress bar moved along nicely until it hit 55%, at which point the connection stalled. Every time I tried it stalled at the same point. The same thing tends to happen for sending other files: it stalls at the same point continually.

If I SFTP through Nautilus I find that I can navigate my remote file system fine, and very quickly, until suddenly it hangs and I can't view a particular folder.

=== /etc/resolv.conf failure ===

Some time ago I installed Debian on my NSLU2 and found that it couldn't resolve the mirrors it needed for the install. In the end it turned out that the nameserver provided by DHCP in /etc/resolv.conf was the router itself which wasn't resolving properly for Debian. Changing this to my ISP's nameservers fixed the problem - but this is not an issue on Windows, which interacts with the router for DNS purposes fine (the router presumably queries my ISP's DNS servers itself and passes the result back).

In Ubuntu I have at times had similar problems so I just use OpenDNS. This issue leads me to believe that my router (a Guru GWART2-54125) is somehow malforming its DHCP packets so that GNU/Linux can't read them, but this is mere speculation; I have no idea how to check further.

Concluding, I have very mysterious problems that are seriously impairing my use of Ubuntu and would appreciate any offered help.

---

### Post by kirilisa on 2010-03-14
Hi,

Did you ever resolve this? I have just recently started having an identical problem. And I really don't want to have to boot into Windows Vista all the time!! :'(

---

### Post by Sean Whitton on 2010-03-15
Basically no, or not with any reliability - I've recently moved house and we've switched from ADSL to Cable DSL, so we've got a different router, and I don't have problems with this one.

The problem did stop when I switched to Debian, but the problem often went when I reinstalled my OS and then returned later, so I don't think Debian is doing anything magical.  Sorry.

---

