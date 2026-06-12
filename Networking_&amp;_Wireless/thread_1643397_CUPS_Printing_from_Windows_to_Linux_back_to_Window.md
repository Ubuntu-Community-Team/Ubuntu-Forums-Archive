---
title: "CUPS: Printing from Windows to Linux back to Windows"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by Theurgist on 2010-12-11
Greetings everybody!

I am new to this forum. I have run Ubuntu for a couple of years, back and forth. Now, I am interested in a solution to a question related to printers, managed through CUPS, _not_ through Samba. I need to use the LPR-protocol.

I wanted to set up at test environment to programatically set up the ports of LPR, to a queue on a Unix system from Windows(however I use Ubuntu for testing on a virtual environment).

I want to send the print from Windows to a lpd:\\192.168...x\queuename that is configured for me in CUPS on a Ubuntu machine that is set up to go back to the Windows-system that has a (Samsung) printer connected to USB, but shared on the environment(a different queue than that one initially started the request).

I am not allowed to use Samba, or any other printing protocol from Windows than LPR/LPD through destination port 515. So please don't bother explaining these concepts to me as I understand that it will solve the problems for some, but will pollute this thread with misleading concepts. Even though I bet it would be conceptually interesting.

The problem is, it seems that Windows doesn't really set up a true LPR/LPD Unix/Linux port when using the prnport.vbs scripts that comes with Windows. However when I do this manually, against the 'professional' Unix system, and connecting the printer via a local port through the printing wizard in Windows and then choosing LPR port, I will get a fully functioning LPR port to the printing server running CUPS.

Now my dilemma, I am working on a completely different system. This system doesn't connect to printers accessed by network, connected directly through TCP/IP via TP-cable, but via a USB shared printer through a Windows computer. That's a relevant difference.

I know, I am begging for trouble, by sending the print, back-and-forth, but the test FROM Ubuntu to Windows works fine (with the printer shared over USB). It doesn't work the other way around however, by sending the print to Linux from Windows.

In Windows it says that it is printing and the print-out does not time-out or alarm any error, but a telnet on 515 gets 'Connect failed'. I have tried to see if there is an issue with Iptables, and has also installed Firestarter to disable the functionality to get rid of any firewall problems.

lpc status gives me that the daemon for the queue is present.

When setting up the LPR port against my CUPS configuration on my test machine(Vista->Ubuntu) I get this:

--------------
The LPD Server did not respond as expected to a test command. Any of the following can cause this error:

The entry for IP Address or Queue Name is incorrect.

The TCP/IP print device (LPD server) does not support the test command.

The specified TCP/IP print device is not available.

If the information typed in the previous screen is correct, you can ignore this message. Click OK to continue, or click Cancel to return to the previous screen and verify settings.
------------------

What am I doing wrong here? Except for doing stuff awkwardly!;)

To me it looks like a firewall issue, but also som trouble with the lpd daemon. As this doesn't happen on the 'professional' system, however I don't have the insight in the actual configuration of CUPS on the server in the 'PRO' environment either, I need your guidance.

A good instinct tells me to narrow it down to only make the queue working from Windows to Linux, however the Linux is on a virtual machine, I don't want to make things more complicated to attach printers through USB via the virtual layers!

Is it practical to stream the LPR port to /dev/null on the Linux side just to see the buffering, to determine any issue with the lpd-daemon, or firewall? However this should be considered secondary if a lot of work is involved with it.

Best regards and thanks in advance!
Theurgist

---

### Post by Theurgist on 2010-12-11
Hi again!

"Still" haven't got this setup to work correctly for me, from Windows to Linux and back. The Linux to Windows part work. I have tried both 9.04 and 10.04, with different results. It seems that the driver differs for the Samsung model, related to CUPS and Ubuntu version. The printer is a Samsung ML-1520. I know this forum was supposed to be about networking. Now this thread is leaning toward both printers and drivers. But it is all about network-printing.

Might it be that the actual driver isn't capable of such a spooling, and redirection of the print-out, and therefor I will never reach a solution to this with the same printer?

Any one experienced with Printers that has a say in this?

Any suggestion or tip?

Is the part of setting a queue in CUPS via lpd://192.168.1.x/samsunglpr a correct way of accessing it through LPR from Windows? I mean, I am setting a queue pointing on the Linux box queue, that is shared and public. No firewall is interupting.

So the Windows machine has a port that is "local" and is an "LPR port", that is pointing to Linux machine IP, and share. That queue is then again pointing to another queue back at the Windows-machine, that is fully functional if you test the communication from the Linux box to that share, but fails when you try to access it through the first windows-queue. I don't even get an indication in the queue, but can see the connection request in firestarter as I toggle it on. I keep firewall off in all other circumstances.

Best regards and thanks in advance!
Theurgist

---

### Post by drdos2006 on 2010-12-12
Which version of Windows are you using ?
Windows 7 has IPP connection removed as far as I know, but XP should work fine.

regards

---

### Post by Theurgist on 2010-12-12
> **drdos2006 said:**
> Which version of Windows are you using ?
Windows 7 has IPP connection removed as far as I know, but XP should work fine.

regards

Thanks for your reply drdos2006!

It's a Vista 32-bit Home Premium system. Upgradeable to Win 7 if I like but I haven't done so yet.

I have included the support for LPR/LPD through Application Wizard (appwiz.cpl) "Turn Windows features on or off". IPP isn't the same thing as LPR/LPD I believe. And there seems to be a difference between Linux LPR and Windows LPR, as when setting up a port through prnport.vbs it will not declare themselves equally in the registry. However I can't just rip that off in registry to hack a new port, it seems, as any such port will not display itself even if I do a restart either of computer or of the print-spool service in Windows. Or do you know something that does the trick? It needs to be a correct LPR-port that actually can communicate with a Solaris system LPR queue. I am actually not 100% sure of the hacking thing, of the registry, why I want to study this behaviour in detail by this test.

Thanks again for your reply,
Theurgist

---

### Post by drdos2006 on 2010-12-12
I just did a google on : windows 7 lpr, hopefully that will guide you better than I can.

regards

---

### Post by Theurgist on 2010-12-12
> **drdos2006 said:**
> I just did a google on : windows 7 lpr, hopefully that will guide you better than I can.

regards

Thanks again for your time and effort drdos!

Thanks for the tip. Unfortunately, Google is out of luck this time it seems. I have digged deep several days. There is a lot of info about setting up LPR queues, but it seems that their configuration works well with any more common LPR settings, as the Windows version has settings for TCP/IP, which is not editable with the more Linux-like LPR-port, with the support added from Application Wizard. It might be that there seems to be some dialect (just guessing, and I might be dead wrong on this) related to Solaris. But now I don't even get my test-setup to work as I thought it would be done. If I can just test something I will have somewhere to go, but right now I am stuck. I will stress that I am not too familiar with CUPS, so the problem might be easier than I think. But I have set the sharing for the printer queues on ofcourse. ;)

Thanks once again,
Theurgist

---

### Post by Theurgist on 2010-12-12
Hi again!

For the purpose of completeness, and to collect information together(for somebody elses' troubles), it actually seems to be a way of editing the registry to make it work. Exporting the parts that I need and changing the names makes it possible to programatically duplicate the ports to a system. With a little care it should be a tiny task to move ports between systems. I have tested to get the ports visible, which didn't "work" previously but now works (or atleast in Vista, I tried in Windows 7 64-bit at the time but the result wasn't as I had hoped at the time - might have been some hang or instability). 

However, now I would like to know if my LPR-queues are possible to set up in the way I did(probably not as they should have worked by the time then - but you might know the correct answer to how this is done?), so that I can finish off this issue as soon as possible.


Thanks in advance!
Theurgist

---

