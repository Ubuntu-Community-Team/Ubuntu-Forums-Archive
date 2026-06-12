---
title: "Major Network issues!!"
date: 2011-02-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Jonny87 on 2011-02-28
Something seems to be worng with natty on my laptop, I don't know what caused it. It was working fine then suddenly after a reboot it was broken,. I tried another reboot (several) just in case was a random bug.

My network icon in the panel won't show but I can still access the menu from it. However the menu won't show any available wireless networks. Also I tried to run updates and update-manager started checking as it does when you start it up, the stops at less than a third of the way in and comes up with the following error.

```

**[SIZE=2]Could not initialize the package information[/SIZE]**

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'
```

If I try to start synaptic, it gives me the same message before it even fully loads then crashes.

Also I'm not sure if its realted but it started the same time, I compiz won't start.

I'll report it as a bug when I know exactly what the bug is. Can someone help me fix this?

---

### Post by cariboo on 2011-02-28
What happens if you remove the file in the error message?

---

### Post by Jonny87 on 2011-03-01
> **cariboo907 said:**
> What happens if you remove the file in the error message?

I get the same error, did I need to refresh or restart anything for that to have an effect or was just a stab in the dark?

---

### Post by cariboo on 2011-03-01
Did you update your package list after the change?

---

### Post by Jonny87 on 2011-03-01
> **cariboo907 said:**
> Did you update your package list after the change?

Nope still no luck, it runs through updating the list then bombs out part way through with much the same message.

---

### Post by Jonny87 on 2011-03-01
I also just realised that its when update manager crashes out after the error, compiz dies.

---

### Post by Jonny87 on 2011-03-01
Fixed.
I deleted everything else in that directory, as seen in the following thread;
[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

---

### Post by ShatPank on 2011-04-05
Sadly that didn't help me at all, anyone got any other tips?

---

### Post by Harry33 on 2011-04-05
Might be something is wrong with the latest Nm update today:
network-manager (0.8.4~git.20110319t175609.d14809b-0ubuntu2)
```

  * debian/control: split libnm-glib2 into a separate binary for the VPN parts
    of the API, the new package will be called libnm-glib-vpn1. (LP: #745769)
  * debian/libnm-glib2.install, debian/libnm-glib-vpn1.install: update to
    correctly install just libnm-glib-vpn.so.* from libnm-glib-vpn1.
  * debian/libnm-glib2.symbols, debian/libnm-glib-vpn1.symbols: move symbol
    definitions for libnm-glib-vpn.so to their own package.
  * debian/control: depend on libnm-glib-vpn1 from libnm-glib2, as a
    transitional measure to maintain compatibility with the VPN plugins.
  * debian/control: have libnm-glib2 and libnm-glib-vpn1 Breaks/Conflicts with
    previous revisions of libnm-glib2, for upgrade purposes.
 -- Mathieu Trudel-Lapierre <email address hidden>   Mon, 04 Apr 2011 22:37:19 -0400

```

You might want to downgrade to the previous version and try booting with that.
Here it is:
[https://launchpad.net/ubuntu/natty/+source/network-manager/0.8.4~git.20110319t175609.d14809b-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/network-manager/0.8.4~git.20110319t175609.d14809b-0ubuntu1)

Addition:
I do not have any issues in my setup using Nm and the latest package:
network-manager (0.8.4~git.20110319t175609.d14809b-0ubuntu2)

---

### Post by ShatPank on 2011-04-05
This is where I always have problems, I have to install that from source yes?? (being tar.gz I mean)
never really understood installing from source, I've not long come from window's and am still used to installers basically, so .deb does me fine normally.

Could you explain how to install that package to me as if I were 5 please...lol

---

### Post by Harry33 on 2011-04-05
> **ShatPank said:**
> This is where I always have problems, I have to install that from source yes?? (being tar.gz I mean)
never really understood installing from source, I've not long come from window's and am still used to installers basically, so .deb does me fine normally.

Could you explain how to install that package to me as if I were 5 please...lol

Packages in Launchpad are already deb packages, so you do not need to compile from source anything.

But, please describe the problem you have before doing anything.
Also say when was the first time you noticed that issue.

---

### Post by ShatPank on 2011-04-05
It all started for me this morning, however I did an update last night (I've been updating nightly since I installed natty) and everything worked fine and no error's popped up, then this morning, I attempted to do an update (I don't remember why considering I've been doing it nightly, think I was jst bored) and I was getting the problem.

When starting the update manager, I instantly get.

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'


If I open a terminal and run "sudo apt-get update" it will refresh a few list's until I get pretty much the same thing.

Fetched 13.2 MB in 2min 42s (81.3 kB/s)                                        
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
stuart@******-Bocks:~$ #

I followed the instructions on the link provided early in this thread, but no change.
Hope that explains a little :)

---

### Post by cariboo on 2011-04-05
Can you open /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_multivers e_i18n_Translation-en with a test editor? eg:

```
sudo gedit /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_multivers e_i18n_Translation-en
```

---

### Post by ShatPank on 2011-04-05
Gedit opens 2 blank tabs, one at /var/lib/apt/lists and another at /home/stuart/
both contain no text what so ever.
However, if I navigate to the list with Nautilus, and open the file in a text editor that way, it's full of load's of rubbish about my router not being connected..... which it is, could something maybe have happened if I tried to connect this morning and the router was down?  I'll post the text from the file.

-----EDIT-----
Coming to think of it, my connection was down for while last night, and that's why I tried to update this morning.


<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
  <title> BT Home Hub</title>
  <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
  <script type="text/javascript">var g_navitem = -1;</script>
  <script type="text/javascript"> var g_focus = -1;</script>
  <script type='text/javascript' src='/cgi/b/ic/util.js'></script>
  <link rel="stylesheet" type="text/css" href="/styles.css">
</head>
<body onLoad="preloadImgs(); setFocus();" bgcolor="#FFFFFF">
  <noscript>
    <h1>BT - BT Home Hub </h1>
    <h4>To view the Web interface of the BT Home Hub, JavaScript must be supported and enabled on your browser! <br><br>Please enable scripting and refresh your browser.</h4>
  </noscript>
  <table cellspacing="0" cellpadding="0" border="0">
    <tr>
      <td colspan="2">
        <table width="100%" cellspacing="0" cellpadding="0" border="0">
          <tr>
             <td align="left"><a href="/"><img src="/images/head_wave.gif" border="0" width="173" height="68" alt="BT broadband"></a></td>
              <td align="right"><a href="/"><img src="/images/title.gif" border="0" width="102" height="68" alt="BT logo"></a></td>             
          </tr>
          <tr>
            <td colspan="2" align="left"><img src="/images/navbar.gif" border="0" width="765" height="40" alt=""></td>
          </tr>
        </table>
      </td>
    </tr>
    <tr>
      <td colspan="2"><img src="/images/spacer.gif" border="0" width="1" height="36" alt=""><br></td>
    </tr>
    <tr>
      <td valign="top" style="height: 100%">
        <script type="text/javascript">writeMenu();</script>
      </td>
      <td valign="top">
        <table cellpadding="0" cellspacing="0" border="0">
           <td rowspan="20"><img src="/images/spacer.gif" border="0" width="25" height="0" alt=""> <script type="text/javascript">writeNavBar();</script> </td>
          <tr>
            <td>
              <table width="560" cellspacing="0" cellpadding="0" border="0">
                <tr>
                  <td>
                   <script type="text/javascript">pm_write_messages();</script> 

<table cellspacing='0' cellpadding='0'><tr><td align='left'><img src='/images/spacer.gif' width='120' alt='' border='0'></td><td align='left'><div class='contentcontainer'>
<form name='intercept_form' action='/cgi/b/ic/connect/' method='post'>
<input type='hidden' name='0' value=''>
<input type='hidden' name='1' value=''>
<input type='hidden' name='2' value='2971399498'>
<table cellspacing='0' cellpadding='0'><tr><td align='left'><span class='itemtitle'>Not Connected...</span></td><td align='right'></td></tr><tr><td colspan='2'><img src='/images/spacer.gif' width='500' height='20' alt='' border='0'></td></tr></table><input type='hidden' name='34' value="gb.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en">
<input type='hidden' name='38' value="DNSSpoofed">
<br><table width='550' class='warnmsg'><tr border><td width='40' valign='left'><img src='/images/alert.gif' alt=''></td><td valign='left'>
<p><h2>Internet Connection not active...</h2><br>We have detected a problem with the setup of your BT Total Broadband.</p>
</td></tr>
<tr><td></td><td><p>1. If you are setting up your BT Home Hub for the first time, please ensure you have followed the instructions from the Getting started guide included in your pack.<br>Please also refer to the Troubleshooting instructions or the User Guide also included in your pack.</p><p>Alternatively please call the technical helpdesk on 0845 600 7030 (call charges apply)</p><p>2. If you read this page when your Broadband connection was working correctly before, then please try the following:<br><ul><li> Your BT Home Hub is not currently connected to the internet. Click on Connect link.<br></li><li>If you have already tried to connect but the connection was unsuccessful, then please check you have the correct Broadband username and password setup. The default is [EMAIL="bthomehub@btbroadband.com"]bthomehub@btbroadband.com[/EMAIL]. No password is necessary.</li><li>The Broadband service may be experiencing a temporary failure. Please try again later.</li></ul></p><p>Click on the link below to connect to the Internet. If the problem persists, you may want to look at the diagnostics page to further investigate the issue.</p>
<table cellspacing='0' cellpadding='0' border='0'>
<tr><td colspan='4'><img src='/images/spacer.gif'  width='500'  height='20' alt='' border='0'></td></tr><tr><td><img src='/images/spacer.gif' width='60' height='5' alt=''></td><td><img src='/images/task__md.gif' width='20' height='20' alt='' border='0'></td><td><img src='/images/spacer.gif' width='20' height='5' alt=''></td><td width='500' class='task'><a href="javascript:submitForm(document.intercept_form,35,4,'','',0,'pb1.start();');">Connect to the Internet</a></td></tr></table>
<table><tr><td><img src='/images/spacer.gif' width='500' height='10' alt='' border='0'></td></tr></table><table cellspacing='0' cellpadding='0' border='0'>
<tr><td colspan='4'><img src='/images/spacer.gif'  width='500'  height='20' alt='' border='0'></td></tr><tr><td><img src='/images/spacer.gif' width='60' height='5' alt=''></td><td><img src='/images/task__md.gif' width='20' height='20' alt='' border='0'></td><td><img src='/images/spacer.gif' width='20' height='5' alt=''></td><td width='500' class='task'><a href="/cgi/b/connchk/?" target="_blank">Troubleshooting</a></td></tr></table>
<table><tr><td><img src='/images/spacer.gif' width='500' height='10' alt='' border='0'></td></tr></table><p><center><script type='text/javascript'>pb1 = new pb({wt:20});</script></center></form>
</tr></td><tr><td colspan='2'><br><table width='550' ><tr><td width='20' valign='left'><img src='/images/desktop_icon.gif' alt=''></td><td valign='left'>
<p>Further diagnostic Help can be found if you have the BT Broadband Desktop Help icon on your desktop or System Tray. Simply double-click the icon to start the application.</p>
</td></tr>
</table> <br></tr></td></table> <br></div>
</td></tr></table>                 </td>
                </tr>
              </table>
            </td>
          </tr>
        </table>
      </td>
    </tr>
    </table>
    <table cellspacing="0">
      <tr>
        <td align="left" colspan="2"><img src="/images/spacer.gif" width="20" height="1" alt=""><img src="/images/spacer.gif" width="10" height="100" alt="A BT  brand"></td>
      </tr>
      <tr>
        <td width="20"></td>
        <td align="left"  background="/images/foot_wave.gif" width="417" height="17"><font color="#FFFFFF"> Software version: 6.2.6.H </font></td>
        <td align="right" background="/images/foot_wave.gif" width="300" height="17"><font color="#FFFFFF"> Time: 05/04/2011 00:42 </font></td>
      </tr>
    </table>
  </body>
</html>

---

### Post by cariboo on 2011-04-05
If that's what's in /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_multivers e_i18n_Translation-en., it's no wonder it doesn't work. I don't have any of  the translation sources on my system, so I can't look at the file here.

---

### Post by Steel-Bunz on 2011-04-05
Trouble here too.. Wireless is disabled in HP Pavilion laptop. Ran update manager last night and restarted the system few mins back. Updated again using Ethernet. Still wireless is disabled. Is there anything I can do to enable the Wireless?

I remember having similar issues with Kubuntu sometime back. By the way, my dual boot Kubuntu is missing too.

---

### Post by ShatPank on 2011-04-05
Yep that's what's in there, or so it seems anyways.
My guess is the internet possibly went down whilst it was fetching list's and for some reason wrote the annoying "your connection is down, click the connect button" page that the Homehub throws out when there's a problem.

Seems very weird that that would actually write to the file though, I can imagine now that I'll get that sorted and it's probably done it to a LOAD of the list's....

Is there a simple way I could repair the list, such as pulling them off the live disc?
Although I can imagine that the list's on my install disk (alpha 3) would be entirely different to what should be in the lists folder anyway and so probably wouldn&#8217;t work.

---

### Post by ShatPank on 2011-04-05
Steel-bunz, do you by any chance have a intel 3945 adapter? my girlfriend's laptop had a similar problem to your description the other day, I'll see if I can find the link that solved it....

This thread was with people having similar problems [http://ubuntuforums.org/showthread.php?t=1718980](http://ubuntuforums.org/showthread.php?t=1718980)

and there's a link on that thread, to THIS thread [http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/](http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/)

The second thread is what fixed my problems, HOWEVER I couldnt get the instruction on the second thread to work, until I replaced "vi" with gedit" like so...

***** NOTE this was for my problem with an INTEL 3945*****

[COLOR=#c20cb9]**```
**[/COLOR]
[COLOR=#c20cb9]** sudo**[/COLOR] [COLOR=#c20cb9]**gedit**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]modrobe.d[COLOR=#000000]**/**[/COLOR]iwl3945
[COLOR=#7a0874]**alias**[/COLOR] wlan0 iwl3945
options iwl3945 [COLOR=#007800]disable_hw_scan[/COLOR]=[COLOR=#000000]1
[/COLOR][COLOR=#c20cb9]**sudo**[/COLOR] modprobe [COLOR=#660033]-r[/COLOR] iwl3945
[COLOR=#c20cb9]**sudo**[/COLOR] modprobe iwl3945

```

Hope that's of some help

---

### Post by Steel-Bunz on 2011-04-05
ShatPank,

Thanks much.. I haven't gone through your post entirely; meanwhile, I have got a solution.. Grabbed it from google search. Ran "rfkill list" and saw that WLAN was 'soft blocked'. Ran the command "rfkill unblock wifi" and voila, I got it back. Still don't understand what went on though.. :(

---

### Post by ShatPank on 2011-04-05
I'm assuming it was the same or a very similar problem as from what I could make out it seemed like a Network Manager update messed up some hardware probing?
I'm not really very "up" on Linux but I'm getting there slowly at last

---

### Post by ShatPank on 2011-04-06
Shameless Bump??

---

