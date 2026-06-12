---
title: "Moonlight Preview 4 fails to download EULA"
date: 2011-02-16
forum: Multimedia Software
---

### Post by mredding on 2011-02-16
When trying to download the Microsoft Media Pack with Moonlight 3.99.0.1, the error "Failed to download EULA, please try again later" appears. 

I used ngrep to determine that it was trying to download [http://go.microsoft.com/fwlink/?LinkId=207083](http://go.microsoft.com/fwlink/?LinkId=207083) which apparently doesn't exist. 

I did some searching, and can't seem to find any posts about the same problem. Anyone else have better luck/suggestions?

EDIT: I imagine a suitable workaround would be to find the URL of the appropriate Media Pack and place the file in ~/.mozilla/plugins/moonlight/ or perhaps obtain it from someone willing to share.

---

### Post by karavago on 2011-02-16
I m looking forward to a workarround to this as well. Not interested in going back to previous versions as i need full silverlight 3 support that only this version of moonlight has. Is there a way to divert the previous url to the correct microsoft site? Well that is if we can the correct url..

---

### Post by avdheiden on 2011-02-16
Same problem here. Tried it with Firefox 3.6 / 4.0beta, Google Chrome and Chromium.

EULA fails to load.

---

### Post by Stampede on 2011-02-16
Same problem. Any idea?

---

### Post by znejk on 2011-02-16
Spoken to a guy on irc who told me that microsoft havnt released the codecs so thats why... they are also waiting for it. 

#silverlight @ irc.gnome.org
<jeff_> we know
 we're waiting for MS to release the codecs

<alan> It was supposed to be done before we released so we're doing the best we can

so just wait ... and i'll miss CL tonight ... damn ms...

---

### Post by znetlive on 2011-02-16
Hey,

I just tried downloading the EULA and I get the same error. Googling around I found the direct link to download the codecs but im not sure which version it downloads. 

I use moonlight 3.99.0.1, on firefox 3.6.13, Ubuntu 10.10 x64

I put the binary in $HOME/.mozilla/plugins/moonlight

I changed chmod the file according to the proper permissions, restarted firefox but it still wouldent load. 

Source:
[http://ossguy.com/?p=266](http://ossguy.com/?p=266)

direct link to ms codecs:
[http://go.microsoft.com/fwlink/?LinkId=133186](http://go.microsoft.com/fwlink/?LinkId=133186) for i386
[http://go.microsoft.com/fwlink/?LinkId=133816](http://go.microsoft.com/fwlink/?LinkId=133816) for x86-64

Please post if you got it working.

---

### Post by suoko on 2011-02-16
> **znetlive said:**
> Hey,

I just tried downloading the EULA and I get the same error. Googling around I found the direct link to download the codecs but im not sure which version it downloads. 

I use moonlight 3.99.0.1, on firefox 3.6.13, Ubuntu 10.10 x64

I put the binary in $HOME/.mozilla/plugins/moonlight

I changed chmod the file according to the proper permissions, restarted firefox but it still wouldent load. 

Source:
[http://ossguy.com/?p=266](http://ossguy.com/?p=266)

direct link to ms codecs:
[http://go.microsoft.com/fwlink/?LinkId=133186](http://go.microsoft.com/fwlink/?LinkId=133186) for i386
[http://go.microsoft.com/fwlink/?LinkId=133816](http://go.microsoft.com/fwlink/?LinkId=133816) for x86-64

Please post if you got it working.

i tried to manually put ms codecs in my chromium directory but i still have eula problems.

---

### Post by gsoundsgood on 2011-02-17
amazing. just had to tic the "don't ask me any more to install the codecs" (or something similar, don't remember exactly) checkbox when I first open a page with silverlight, and it magically finds the EULA, installs the codecs and... well, updated silverlight just works!

---

### Post by FearTheNoFear on 2011-02-17
Today it works by showing the EULA but last night it didn't. I now have sound but no video still. Stupid online classes needing to use Silverlight.

---

### Post by anotherone33 on 2011-02-18
Hy guys.
I succeed in installing moonlight/silverlight and going through process of installing codecs + eula, making working everything.

I ask your collaboration for making reproducible to everybody wanting it.  If you succeed in doing it working also for you, following something of my post, the price I ask for that, it is sharing it, if that can add something in making a better and simpler procedure.

I add to this post some crucial pictures of the installation process but it is not possible attaching the silverlight-media-pack-linux-x64-21-1.so because his weight 4.4 Mb, and also tar.bz2 is 1.5 Mb.  md5sum is: 137d3ec1d3db7ce971650c22099db867  silverlight-media-pack-linux-x64-21-1.so

Working with: Firefox plugin Novell Moonlight 3.99.0.1 and silverlight-media-pack-linux-x64-21-1.so, Silverlight plugin 4.0.50917.0, Ubuntu 10.04.2 LTS x64, last Firefox 3.6.13

I don't know exactly moonlight and silverlight working.

1. Install [Novell Moonlight 3.99.0.1]("http://go-mono.com/moonlight/download.aspx") ([http://go-mono.com/moonlight/download.aspx](http://go-mono.com/moonlight/download.aspx)) and Silverlight ...

2. going through process of installing wma codecs and accepting eula: you need in some part of process higher rights than user. I noted it installs version silverlight-media-pack-linux-x64-21-1.so in ~/.mozilla/plugins/moonlight/

Here I'm a little confused on procedure. In trying to make it working I tried web guides I found. I did a lot of tries, maybe one of them it is fundamental, I don't know, I cannot reproduce or remember. 
When I right clicked on empty video (not still working) with Moonlight logo at center, then on "Novell Moonlight 3.99.0.1", then "Playback" section, then Install Microsoft Media Pack, the process halt with a undefined "network error" when trying to getting EULA. I thought root rights needed to make installation ... but how to give them to the process if not provided with a dialog ?
So I tried Firefox with root rights ... $sudo firefox .... the process can get EULA, dialog with accept button, then the process continue getting codecs. Working for root. In shell I could see downloading and copying silverlight-media-pack-linux-x64-21-1.so So I copied it to my user ~/.mozilla/plugins/moonlight/ , then I had to change the rights of file to my user owner (chown) and rights (chmod +x  ? rwx ?). In some part may be it is needed restart firefox and again trying the process getting codecs and installing them.  Then a final dialog tell you to refresh the page with Silverlight/Moonlight video ... and then all working.

Cheers,
M.

---

### Post by anotherone33 on 2011-02-27
hi,
some configuration in Ubuntu 10.04 lts, last firefox 3.6.8
just installed moonlight from [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)  -> [http://www.go-mono.com/moonlight/download.aspx](http://www.go-mono.com/moonlight/download.aspx) ; Firefox plugin Novell Moonlight 3.99.0.1 , Silverlight plugin 4.0.50917.0,

all installation without problems, getting eula, installing sw (probably silverlight-media-pack-linux-x86-21-1.so with rwx only rights automatically). md5sum 7ca7b43bf117756cc64698ab5f247353  silverlight-media-pack-linux-x86-21-1.so

But then, when on silverlight ... crashing firefox 

these the messages:

```
~/.mozilla/plugins/moonlight$ firefox 
Moonlight: 3.99.0.1
Moonlight: Attempting to load libmoonloaderxpi 
debug_get_option: GALLIUM_DRIVER = softpipe
couldn't open libtxc_dxtn.so, software DXTn compression/decompression unavailable
Moonlight: no audio capture service available
Moonlight: Installing signal handlers for crash reporting.
Moonlight: Enabling MONO_DEBUG=keep-delegates,reverse-pinvoke-exceptions and MOONLIGHT_ENABLE_CONSOLE=1
Moonlight: Loaded mscodecs from: ~/.mozilla/plugins/moonlight/silverlight-media-pack-linux-x86-21-1.so.
Using the ff3 bridge
Moonlight: Plugin AppDomain Creation: OK
Moonlight: URL = http://www.rai.tv/dl/RaiTV/diretta.html?cid=PublishingBlock-eedb4649-b6c4-4892-a5a9-e2ca63b54bd8&channel=Rai 3#cid=PublishingBlock-eedb4649-b6c4-4892-a5a9-e2ca63b54bd8
Moonlight: URL = http://www.rai.tv/dl/objects/silverlight/uniplayer/Rai.UniPlayer.xap
Moonlight: OpenGL vendor string: Mesa Project
Moonlight: OpenGL renderer string: Software Rasterizer
Moonlight: OpenGL version string: 2.1 Mesa 7.7.1
Using native xaml parser.
trying to load: /Microsoft.Web.Media.SmoothStreaming;component/themes/generic.xaml
trying to load: /Microsoft.SilverlightMediaFramework.Player;component/themes/generic.xaml
trying to load: /System.Windows;component/themes/generic.xaml
Moonlight: Unhandled exception in Events.SafeAction: System.ArgumentException: Value must be greater than zero
  at Mono.NativeMethods.dependency_object_set_value (IntPtr instance, IntPtr property, Mono.Value& value) [0x00000] in <filename unknown>:0 
  at Mono.NativeDependencyObjectHelper.SetValue (INativeDependencyObjectWrapper wrapper, System.Windows.DependencyProperty dp, System.Object value) [0x00000] in <filename unknown>:0 
  at System.Windows.DependencyObject.SetValueImpl (System.Windows.DependencyProperty dp, System.Object value) [0x00000] in <filename unknown>:0 
trying to load: /System.Windows.Controls.Layout.Toolkit;component/themes/generic.xaml

Unhandled Exception: System.ExecutionEngineException: SIGILL

```

anyone ? no idea on how to solve ?

---

### Post by anotherone33 on 2011-02-27
updating to firefox 3.6.13

installing update-manager  (sudo apt-get install update-manager)

updating with update-manager... ok


but again firefox crashing.  no effect with root privileges :

```
Moonlight: 3.99.0.1
Moonlight: Attempting to load libmoonloaderxpi 
debug_get_option: GALLIUM_DRIVER = softpipe
couldn't open libtxc_dxtn.so, software DXTn compression/decompression unavailable
Moonlight: no audio capture service available
Moonlight: Installing signal handlers for crash reporting.
Moonlight: Enabling MONO_DEBUG=keep-delegates,reverse-pinvoke-exceptions and MOONLIGHT_ENABLE_CONSOLE=1
Moonlight: Cannot load silverlight-media-pack-linux-x86-21-1.so: silverlight-media-pack-linux-x86-21-1.so: impossibile aprire il file oggetto condiviso: File o directory non esistente
Using the ff3 bridge
Moonlight: Plugin AppDomain Creation: OK
Moonlight: URL = http://www.rai.tv/dl/RaiTV/diretta.html?cid=PublishingBlock-eedb4649-b6c4-4892-a5a9-e2ca63b54bd8&channel=Rai 3#cid=PublishingBlock-eedb4649-b6c4-4892-a5a9-e2ca63b54bd8
Moonlight: URL = http://www.rai.tv/dl/objects/silverlight/uniplayer/Rai.UniPlayer.xap
Moonlight: OpenGL vendor string: Mesa Project
Moonlight: OpenGL renderer string: Software Rasterizer
Moonlight: OpenGL version string: 2.1 Mesa 7.7.1
Using native xaml parser.
trying to load: /Microsoft.Web.Media.SmoothStreaming;component/themes/generic.xaml
trying to load: /Microsoft.SilverlightMediaFramework.Player;component/themes/generic.xaml
trying to load: /System.Windows;component/themes/generic.xaml
Moonlight: Unhandled exception in Events.SafeAction: System.ArgumentException: Value must be greater than zero
  at Mono.NativeMethods.dependency_object_set_value (IntPtr instance, IntPtr property, Mono.Value& value) [0x00000] in <filename unknown>:0 
  at Mono.NativeDependencyObjectHelper.SetValue (INativeDependencyObjectWrapper wrapper, System.Windows.DependencyProperty dp, System.Object value) [0x00000] in <filename unknown>:0 
  at System.Windows.DependencyObject.SetValueImpl (System.Windows.DependencyProperty dp, System.Object value) [0x00000] in <filename unknown>:0 
trying to load: /System.Windows.Controls.Layout.Toolkit;component/themes/generic.xaml
AudioPlayer: Using PulseAudio.
PulsePlayer::InitializeInternal (): initialization took 2 ms
Moonlight: Loaded mscodecs from: /root/.mozilla/plugins/moonlight/silverlight-media-pack-linux-x86-21-1.so.
Moonlight: Shutting down
Using the ff3 bridge
Moonlight: Plugin AppDomain Creation: OK
Moonlight: URL = http://www.rai.tv/dl/RaiTV/diretta.html?cid=PublishingBlock-eedb4649-b6c4-4892-a5a9-e2ca63b54bd8&channel=Rai 3#cid=PublishingBlock-eedb4649-b6c4-4892-a5a9-e2ca63b54bd8
Moonlight: URL = http://www.rai.tv/dl/objects/silverlight/uniplayer/Rai.UniPlayer.xap
Moonlight: OpenGL vendor string: Mesa Project
Moonlight: OpenGL renderer string: Software Rasterizer
Moonlight: OpenGL version string: 2.1 Mesa 7.7.1
Using native xaml parser.
trying to load: /Microsoft.Web.Media.SmoothStreaming;component/themes/generic.xaml
trying to load: /Microsoft.SilverlightMediaFramework.Player;component/themes/generic.xaml
trying to load: /System.Windows;component/themes/generic.xaml
Moonlight: Unhandled exception in Events.SafeAction: System.ArgumentException: Value must be greater than zero
  at Mono.NativeMethods.dependency_object_set_value (IntPtr instance, IntPtr property, Mono.Value& value) [0x00000] in <filename unknown>:0 
  at Mono.NativeDependencyObjectHelper.SetValue (INativeDependencyObjectWrapper wrapper, System.Windows.DependencyProperty dp, System.Object value) [0x00000] in <filename unknown>:0 
  at System.Windows.DependencyObject.SetValueImpl (System.Windows.DependencyProperty dp, System.Object value) [0x00000] in <filename unknown>:0 
trying to load: /System.Windows.Controls.Layout.Toolkit;component/themes/generic.xaml

Unhandled Exception: System.ExecutionEngineException: SIGILL

```

---

