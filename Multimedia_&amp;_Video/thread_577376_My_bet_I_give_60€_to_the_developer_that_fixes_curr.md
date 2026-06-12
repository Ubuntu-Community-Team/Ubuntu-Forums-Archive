---
title: "My bet: I give 60€ to the developer that fixes current 3D bugs in Unichrome PRO"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by ringmaster on 2007-10-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/xorg-server/+bug/43154/](https://bugs.launchpad.net/xorg-server/+bug/43154/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**WE NEED 3D**, it is becoming essential on desktop (Compiz fussion, games, Screensavers), so the faster way to fix this is to encourage a developer. I don't know if there is another place to make this money-driven post, please feel free to advise me, and feel free to join this effort also, your euro/dollar is important too.

I know that the more important open source developers are working for companies, and I know that the need to eat :popcorn: so this could be a valid way to redirect efforts to this cause :(

**The problem in more detail:**

There is a [_known and old problem_]("https://bugs.launchpad.net/xorg-server/+bug/43154/") with the Unichrome PRO series drivers (CLE266, KN400, KM400, K8M800, PM800, CN400, VN800, CN700, CX700, and so on).
These cards are **widely used in budget computers** (e.g. laptops), or integrated into motherboard (e.g. mini-ITX ones) so please don't suggest buying a new one.
For example, my CN700 freezes Xserver whenever I use opengl (it can work for half an hour, but lockups xorg 7.2 ramdomly every time). The keyboard and mouse are unresponsive, so I can't restart xserver (but the kernel continues to work as I can see for the hd and net activity; I could telnet).

I think they are only a few bugs 'cause it doesn't lockup inmediately, so it is fixable. VIA is not friendly (I can see complaints from developers for their obscurity about hardware specifications) but having the [_open source drivers from VIA_]("http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=158") (althout they're messy and buggy) should help a lot ([_if available_]("http://forums.viaarena.com/messageview.aspx?catid=28&threadid=78349&highlight_key=y&keyword1=k8M800")).

I am going to try to help using this guides, and probably attach the info to the [_bug in Launchpad_]("https://bugs.launchpad.net/xorg-server/+bug/43154/"):
[_TriagingXBugs_]("https://wiki.ubuntu.com/TriagingXBugs")
[_DebuggingXAutoconfiguration_]("https://help.ubuntu.com/community/DebuggingXAutoconfiguration") (not very related).
Probably I will need another computer to login into the system and debug it. I am a user, but I can learn to use gdb (I helped before other projects). I am willing to help to the developers to test the code in my machine if they need to.

Bugs [_related to this one_]("https://bugs.launchpad.net/xorg-server/+bug/43154/") (probably duplicates):
[_f-spot freezes when using hardware acceleration_]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-unichrome/+bug/89467")
[_glxinfo crashes with SIGSEV_]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/122999")
[_Please provide 3D rectricted driver_]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/122762")
[_Ubuntu 6.06 hangs with OpenGL screensaver_]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/107504")
[_Clicking in OpenGL in Kinfocenter freezes the system_]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/132000")

Posts related to this problematic via driver, too:
[_VIA EPIA Analysis: Gráficos acelerados por HW from Vicente Navarro (spanish)_]("http://www.vicente-navarro.com/blog/index.php/2007/10/10/sobre-las-via-epia-vi-graficos-y-video-acelerado-por-hw-en-linux-con-la-ex10000eg/")
[_VIA S3G UniChrome Pro IGP_]("http://ubuntuforums.org/showthread.php?t=342115&highlight=unichrome+pro")
[_Need help with 3D rendering and video_]("http://ubuntuforums.org/showthread.php?t=465298")
[_3D with VIA driver doesn't work_]("http://ubuntuforums.org/showthread.php?t=470044&highlight=unichrome+pro")
[_S3 Graphics UniChrome&#8482; Pro IGP Series w/ Compiz_]("http://ubuntuforums.org/showthread.php?t=525553&highlight=unichrome+pro")
[_S3 Graphics UniChrome&#8482; Pro IGP Series_]("http://ubuntuforums.org/showthread.php?t=525045&highlight=unichrome+pro")
and so on...

The payment will be made with Paypal preferably (distributed into the developers depending on work/quality of fixes), but transference is other possibility. [B][COLOR="Red"]This is a serious thread, if you post a contribution please carry it to the end with all the consequences or avoid this thread.
[/COLOR][/B]
Kind regards from spain,

David Losada

---

