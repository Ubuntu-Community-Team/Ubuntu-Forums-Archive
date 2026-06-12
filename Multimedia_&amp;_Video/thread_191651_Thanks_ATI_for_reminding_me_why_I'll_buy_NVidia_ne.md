---
title: "Thanks ATI for reminding me why I'll buy NVidia next time"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by baldass_newbie on 2006-06-07
/rant on
Overall I've been very happy with Dapper Drake.  I was even impressed that I got a decent resolution after the upgrade.  
However, this pain with fglrx and ati and whatnot for drivers and trying to get acceleration just reminds me why I should have gotten and next time will get an nvidia card.  

You would think ATI would have gotten their act together and worked with the Linux community to deliver a painless experience.  No, you can't please everybody, but I've been hacking on the penguin since RedHat 4 and, outside of winmodems, ATI cards are the single biggest hardware headache.  
Sure, maybe I got a niche or a cheap card (it was a gift.)  But that doesn't mean it should operate like utter garbage.  

Just venting and I'm sure others are feeling my pain.  But I cannot believe ATI can deliver so well for OS X and decent enough for Windows but insists on laying a turd on the Linux community.  

Otherwise, I am very close to dumping my XP machine.  I really don't want to have to deal with Vista and I'm committed to finding everything I need and making it work, most likely with Ubuntu.  

But there's no excuse for poor hardware support.  Sorry.  It's not like the Linux folks are hiding their code, either.  

Hey, ATI, take your stinkin' RPMs and stick them where the sun don't shine.  

/rant off

---

### Post by BLTicklemonster on 2006-06-07
I'm with you on this one. 

I have downloaded dapper and will be taking the plunge again soon. This time with my nvidia card, not one of the SEVERAL ati 128 meg cards sitting on the shelf here gathering dust.

I tried several different times to install ati drivers on THE SAME MACHINE in ubuntu (reinstalls after my noob *** messed things up beyond all repair) and not one single time with the exception of the first time of course (using the exact steps that worked the first time for me) was I able to get the ati card to run correctly.

---

### Post by RussianVodka on 2006-06-07
I installed fglrx on my brothers system which uses a Radeon 9800pro with an XT core. And it worked fine. Then again I completely killed the OS when trying to install Compiz, but that's a different story...

The thing that I can't figure out is how to solve the problem with the artifacts on my system, which uses a Radeon 7500.

---

### Post by kakashi on 2006-06-08
[QUOTE=baldass_newbie]/rant on
Overall I've been very happy with Dapper Drake.  I was even impressed that I got a decent resolution after the upgrade.  
However, this pain with fglrx and ati and whatnot for drivers and trying to get acceleration just reminds me why I should have gotten and next time will get an nvidia card.  

You would think ATI would have gotten their act together and worked with the Linux community to deliver a painless experience.  No, you can't please everybody, but I've been hacking on the penguin since RedHat 4 and, outside of winmodems, ATI cards are the single biggest hardware headache.  
Sure, maybe I got a niche or a cheap card (it was a gift.)  But that doesn't mean it should operate like utter garbage.  

Just venting and I'm sure others are feeling my pain.  But I cannot believe ATI can deliver so well for OS X and decent enough for Windows but insists on laying a turd on the Linux community.  

Otherwise, I am very close to dumping my XP machine.  I really don't want to have to deal with Vista and I'm committed to finding everything I need and making it work, most likely with Ubuntu.  

But there's no excuse for poor hardware support.  Sorry.  It's not like the Linux folks are hiding their code, either.  

Hey, ATI, take your stinkin' RPMs and stick them where the sun don't shine.  

/rant off[/QUOTE]

umm i got 3d acceleration working pretty easyily. what did you do. maybe we can help. 
hwere what i did. 
download the driver from ati.com
[QUOTE=from wiki]
Using the drivers from ati.com

As of november 2005, ATI provides usable, properly packaged drivers which can be used on Ubuntu. They can even be installed easily!

   1.

      Download the apropiate drivers from [WWW] ati.com. You will need the ATI Driver Installer, not the seperate XFree86/X.org rpm packages. Save the installer into an empty directory (or at least one containing no *.deb files), since it will create several new files.
   2.

      Make sure the universe section of the Ubuntu repositories is enabled (See the AddingRepositoriesHowto)
   3.

      Perform the following commands (where <version> is the version number of the installer):

      sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper
      chmod +x ati-driver-installer-<version>.run
      fakeroot ./ati-driver-installer-<version>.run

Choose "Generate distribution specific packages" and "Ubuntu" and the Ubuntu version you use. If your window is too small for you to see all of the options use Alt+LeftMouseButton on the window to move it out of the screen's boundaries. (Gnome, and KDE)

sudo dpkg -i *.deb
sudo module-assistant build,install fglrx-kernel
reboot

[/QUOTE]

---

### Post by campnic on 2006-06-08
I'm trying to follow your method.  The installer fails with errors.  It says that the log will be in /usr/share/fglrx/ but it ends up being in (my home diretory)/usr/share/fglrx/ and it says"
```

/tmp/fglrx.osgYII ~/Desktop/ati driver/fglrx-install
Package build failed!
Package build utility output:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
~/Desktop/ati driver/fglrx-install
[Error] Generate Package - error generating package : Ubuntu/6.06

```

Any ideas?

---

### Post by ubuntu27 on 2006-06-08
The rant Reminds me of 

"when Richard Stallman learned that a compiler architect from ATI would be speaking at MIT, he immediately started organizing a protest against ATI's damaging free software policies."

[http://gaming.gwos.org/index.php?option=com_content&task=view&id=28&Itemid=1](http://gaming.gwos.org/index.php?option=com_content&task=view&id=28&Itemid=1)

---

### Post by flipkick on 2006-06-08
It's is really a pain in whatever you think of.

Sorry I can't help here with technical aspects, since I struggle hard wit my Radeon 9800 Pro.

If I only had bought an NVidia Card, I could focus on my work, merely than produce work.

So long keep up the faith of it :)

---

### Post by scxtt on 2006-06-08
i had ZERO luck getting fglrx working in the past - even used directions off these forums in the past -- then i stumbled upon directions, which i think i found on a wiki (just copied and pasted them, to save, don't have the url) ... it's worked time and again in both breezy and dapper (only a minor change to get it to work in dapper) ... i can post the directions if anyone is interested in yet another fglrx method ...

but my X850Pro is pumping out +1300FPS in fgl_glxgears ...

it seems to hinge mostly on the module assistant (using the .run available from ATI's linux download area) and making sure you compile the kernel module for fglrx ...

---

### Post by acankat on 2006-06-08
I'm getting desperate in this fglrx thing, post it as soon as possible please. I'll completely dump windoez as soon as I solve this problen (If I ever can)

---

### Post by scxtt on 2006-06-08
[QUOTE=acankat]I'm getting desperate in this fglrx thing, post it as soon as possible please. I'll completely dump windoez as soon as I solve this problen (If I ever can)[/QUOTE]

i found a link in another thread that's very close to the directions i've used, starting w/ "Method 2: ...":

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

saw it here: [http://www.ubuntuforums.org/showpost.php?p=1110332&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1110332&postcount=2)

---

### Post by kakashi on 2006-06-08
are you using the amd64 version ?
cuz i got plenty of errors last time i tired that. try the i386 version if your not already. 
also

---

### Post by arkangel on 2006-06-08
I am  with you too  i innocently bought a  laptop  with ati card ,  i solved some of my problems  with dapper  but not thanks to ati bfore i had a dell  with  nvidia  and with 2 clicks  i had it working on perfect

---

### Post by Mr Green on 2006-06-08
I don't even bother installing the ATI drivers anymore. It messes up Remote Desktop and I don't really play games on Ubuntu. For that I have my wintendo partition.

But in Dapper I can actually use ctrl-alt-backspace without having the monitor go black with the ATI drivers =D>

But I will most certainly never again buy an ATI card!

I guess NVIDIA is gonna be big in China!

---

### Post by brickhead20 on 2006-06-08
GAHHH! DAMN YOU! I had my ATI working fine on 5.10, but I can't get X-server running AT ALL on 6.06. I can't even use the ruddy vesa drivers, so I can't even reinstall the ATI proprietary ones (is there a way from the command line)! Why can't they just work with it. I'm trying a fresh reinstall, currently downloading the iso (in windows *wretches). *Prays

However, 56k winmodems were possibly, 10000000x worse :D, and atleast the command line saved my butt for backing up stuff. SuSe install wont even run lol!

---

### Post by baldass_newbie on 2006-06-08
[QUOTE=kakashi]umm i got 3d acceleration working pretty easyily. what did you do. maybe we can help. 
hwere what i did. 
download the driver from ati.com[/QUOTE]
kakashi, 

I tried to re-run this morning, but I think I have to uninstall my existing drivers.  Following your example I was actually able to get the dialog box to open, which is a nice change, however, I still cannot run fgl_glxgears.  I was going to post the output but I had to catch the train.  

I will go through it again tonight and post results.  

Regardless, I still hold it shouldn't be this difficult.  Not at this point.

---

### Post by baldass_newbie on 2006-06-08
[QUOTE=kakashi]umm i got 3d acceleration working pretty easyily. what did you do. maybe we can help. 
hwere what i did. 
download the driver from ati.com[/QUOTE]

I'll take you up on your offer (or anyone else who wants to lend a hand.)  

I ran what you outlined, however, when I go to install, I get the following:

```
user@computer:~/ati$ sudo dpkg -i *.deb
(Reading database ... 104772 files and directories currently installed.)
Preparing to replace fglrx-control 8.25.18-1 (using fglrx-control_8.25.18-1_i386.deb) ...
Unpacking replacement fglrx-control ...
Preparing to replace fglrx-kernel-source 8.25.18-1 (using fglrx-kernel-source_8.25.18-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Preparing to replace fglrx-sources 8.25.18-1 (using fglrx-sources_8.25.18-1_i386.deb) ...
Unpacking replacement fglrx-sources ...
Preparing to replace xorg-driver-fglrx 8.25.18-1 (using xorg-driver-fglrx_8.25.18-1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
Preparing to replace xorg-driver-fglrx-dev 8.25.18-1 (using xorg-driver-fglrx-dev_8.25.18-1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Setting up fglrx-kernel-source (8.25.18-1) ...
Setting up fglrx-sources (8.25.18-1) ...
Setting up xorg-driver-fglrx (8.25.18-1) ...

Setting up xorg-driver-fglrx-dev (8.25.18-1) ...
Setting up fglrx-control (8.25.18-1) ...
user@computer:~/ati$ sudo module-assistant build,install fglrx-kernel
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Target package file
/usr/src/fglrx-kernel-2.6.15-23-386_8.25.18-1+2.6.15-23.39_i386.deb already
exists, not rebuilding!
Version 8.25.18-1+2.6.15-23.39 of fglrx-kernel-2.6.15-23-386 already installed, skipping.
```

Should I uninstall the fglrx-kernel via Synaptic?  

FWIW, when I run fglrxinfo, I get the following:  

```
user@computer:~/ati$ fglrxinfo
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3sATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3svATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3iATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3ivATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dvATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementsEXT
[fglrx] API ERROR: could not register entrypoint for WeightbvARB
[fglrx] API ERROR: could not register entrypoint for WeightsvARB
[fglrx] API ERROR: could not register entrypoint for WeightivARB
[fglrx] API ERROR: could not register entrypoint for WeightfvARB
[fglrx] API ERROR: could not register entrypoint for WeightdvARB
[fglrx] API ERROR: could not register entrypoint for WeightubvARB
[fglrx] API ERROR: could not register entrypoint for WeightusvARB
[fglrx] API ERROR: could not register entrypoint for WeightuivARB
[fglrx] API ERROR: could not register entrypoint for WeightPointerARB
[fglrx] API ERROR: could not register entrypoint for VertexBlendARB
[fglrx] API ERROR: could not register entrypoint for MultiDrawArraysEXT
[fglrx] API ERROR: could not register entrypoint for MultiDrawElementsEXT
[fglrx] API ERROR: could not register entrypoint for DrawBuffersATI
[fglrx] API ERROR: could not register entrypoint for DrawElementsFGL
[fglrx] API ERROR: could not register entrypoint for DrawWireTrianglesFGL
[fglrx] API ERROR: could not register entrypoint for PNTrianglesiATI
[fglrx] API ERROR: could not register entrypoint for PNTrianglesfATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for BeginVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for EndVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for BindVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for GenVertexShadersEXT
[fglrx] API ERROR: could not register entrypoint for DeleteVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp1EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp2EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp3EXT
[fglrx] API ERROR: could not register entrypoint for SwizzleEXT
[fglrx] API ERROR: could not register entrypoint for WriteMaskEXT
[fglrx] API ERROR: could not register entrypoint for InsertComponentEXT
[fglrx] API ERROR: could not register entrypoint for ExtractComponentEXT
[fglrx] API ERROR: could not register entrypoint for GenSymbolsEXT
[fglrx] API ERROR: could not register entrypoint for SetInvariantEXT
[fglrx] API ERROR: could not register entrypoint for SetLocalConstantEXT
[fglrx] API ERROR: could not register entrypoint for VariantbvEXT
[fglrx] API ERROR: could not register entrypoint for VariantsvEXT
[fglrx] API ERROR: could not register entrypoint for VariantivEXT
[fglrx] API ERROR: could not register entrypoint for VariantfvEXT
[fglrx] API ERROR: could not register entrypoint for VariantdvEXT
[fglrx] API ERROR: could not register entrypoint for VariantubvEXT
[fglrx] API ERROR: could not register entrypoint for VariantusvEXT
[fglrx] API ERROR: could not register entrypoint for VariantuivEXT
[fglrx] API ERROR: could not register entrypoint for VariantPointerEXT
[fglrx] API ERROR: could not register entrypoint for EnableVariantClientStateEXT[fglrx] API ERROR: could not register entrypoint for DisableVariantClientStateEXT
[fglrx] API ERROR: could not register entrypoint for BindLightParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindMaterialParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTexGenParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTextureUnitParameterEXT[fglrx] API ERROR: could not register entrypoint for BindParameterEXT
[fglrx] API ERROR: could not register entrypoint for IsVariantEnabledEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantPointervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantBooleanvEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantIntegervEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for WindowPos2dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2dvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dvARB
[fglrx] API ERROR: could not register entrypoint for BindBufferARB
[fglrx] API ERROR: could not register entrypoint for DeleteBuffersARB
[fglrx] API ERROR: could not register entrypoint for GenBuffersARB
[fglrx] API ERROR: could not register entrypoint for IsBufferARB
[fglrx] API ERROR: could not register entrypoint for BufferDataARB
[fglrx] API ERROR: could not register entrypoint for BufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for GetBufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for MapBufferARB
[fglrx] API ERROR: could not register entrypoint for UnmapBufferARB
[fglrx] API ERROR: could not register entrypoint for GetBufferParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetBufferPointervARB
[fglrx] API ERROR: could not register entrypoint for NewObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for IsObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UpdateObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferfvATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferivATI
[fglrx] API ERROR: could not register entrypoint for FreeObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for DeleteObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for ArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VariantArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for ElementPointerATI
[fglrx] API ERROR: could not register entrypoint for DrawElementArrayATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementArrayATI
[fglrx] API ERROR: could not register entrypoint for MapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UnmapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for VertexAttribArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4bvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4usvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4uivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NbvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NsvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NusvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NuivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttribPointerARB
[fglrx] API ERROR: could not register entrypoint for EnableVertexAttribArrayARB
[fglrx] API ERROR: could not register entrypoint for DisableVertexAttribArrayARB[fglrx] API ERROR: could not register entrypoint for ProgramStringARB
[fglrx] API ERROR: could not register entrypoint for BindProgramARB
[fglrx] API ERROR: could not register entrypoint for DeleteProgramsARB
[fglrx] API ERROR: could not register entrypoint for GenProgramsARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramivARB
[fglrx] API ERROR: could not register entrypoint for GetProgramStringARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribdvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribfvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribivARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribPointervARB
[fglrx] API ERROR: could not register entrypoint for IsProgramARB
[fglrx] API ERROR: could not register entrypoint for GenFragmentShadersATI
[fglrx] API ERROR: could not register entrypoint for BindFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for DeleteFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for BeginFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for EndFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for PassTexCoordATI
[fglrx] API ERROR: could not register entrypoint for SampleMapATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for SetFragmentShaderConstantATI
[fglrx] API ERROR: could not register entrypoint for CurrentPaletteMatrixARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexubvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexusvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexuivARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexPointerARB
[fglrx] API ERROR: could not register entrypoint for StencilOpSeparateATI
[fglrx] API ERROR: could not register entrypoint for StencilFuncSeparateATI
[fglrx] API ERROR: could not register entrypoint for PointParameteriEXT
[fglrx] API ERROR: could not register entrypoint for PointParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for DeleteOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for IsOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for BeginOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for EndOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryivNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryuivNV
[fglrx] API ERROR: could not register entrypoint for MapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for UnmapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for PointParameterfARB
[fglrx] API ERROR: could not register entrypoint for PointParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GenVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for DeleteVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for BeginDefineVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndDefineVisibilityQueryATI[fglrx] API ERROR: could not register entrypoint for BeginUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for GenQueriesARB
[fglrx] API ERROR: could not register entrypoint for DeleteQueriesARB
[fglrx] API ERROR: could not register entrypoint for IsQueryARB
[fglrx] API ERROR: could not register entrypoint for BeginQueryARB
[fglrx] API ERROR: could not register entrypoint for EndQueryARB
[fglrx] API ERROR: could not register entrypoint for GetQueryivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectuivARB
[fglrx] API ERROR: could not register entrypoint for DeleteObjectARB
[fglrx] API ERROR: could not register entrypoint for GetHandleARB
[fglrx] API ERROR: could not register entrypoint for DetachObjectARB
[fglrx] API ERROR: could not register entrypoint for CreateShaderObjectARB
[fglrx] API ERROR: could not register entrypoint for ShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for CompileShaderARB
[fglrx] API ERROR: could not register entrypoint for CreateProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for AttachObjectARB
[fglrx] API ERROR: could not register entrypoint for LinkProgramARB
[fglrx] API ERROR: could not register entrypoint for UseProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for ValidateProgramARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fARB
[fglrx] API ERROR: could not register entrypoint for Uniform1iARB
[fglrx] API ERROR: could not register entrypoint for Uniform2iARB
[fglrx] API ERROR: could not register entrypoint for Uniform3iARB
[fglrx] API ERROR: could not register entrypoint for Uniform4iARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform1ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform2ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform3ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform4ivARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix2fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix3fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix4fvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetInfoLogARB
[fglrx] API ERROR: could not register entrypoint for GetAttachedObjectsARB
[fglrx] API ERROR: could not register entrypoint for GetUniformLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveUniformARB
[fglrx] API ERROR: could not register entrypoint for GetUniformfvARB
[fglrx] API ERROR: could not register entrypoint for GetUniformivARB
[fglrx] API ERROR: could not register entrypoint for GetShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for BindAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveAttribARB
[fglrx] API ERROR: could not register entrypoint for GetAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for IsRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for BindRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for RenderbufferStorageEXT
[fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivEXT
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT
```

I'm game for anything.  I've gone through the [wiki HOWTO]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI").  
I've gone through the [unofficial ATI Ubuntu Dapper installation guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").  
I don't care if I have to compile, manually configure, work in a terminal with no X Windows, whatever.  
What am I doing wrong and what could I do THAT WILL WORK?!?!

(In the meantime I'll go lurking and looking for someone who might have gotten this shnizz to work.)
](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by baldass_newbie on 2006-06-08
Alright, I just retried the steps from the [Unofficial ATI Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") (why do I get different results each time?) and I got the following output.  

I manually updated the /etc/X11/xorg.conf  from 'fglrx' to 'ati' and when I tried to run fglrxinfo, I received the same error outlined above.  So then I tried the following per the instructions.  

```
user@computer:~/ati$ dmesg | grep fglrx
[4294695.834000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies , Starnberg, GERMANY' taints kernel.
[4294695.835000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294695.835000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294696.746000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294696.746000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294696.746000] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of  chipset)
[4294696.747000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[4294696.754000] [fglrx] total      GART = 33554432
[4294696.754000] [fglrx] free       GART = 17559552
[4294696.754000] [fglrx] max single GART = 17559552
[4294696.754000] [fglrx] total      LFB  = 124436480
[4294696.754000] [fglrx] free       LFB  = 109076480
[4294696.754000] [fglrx] max single LFB  = 109076480
[4294696.754000] [fglrx] total      Inv  = 0
[4294696.754000] [fglrx] free       Inv  = 0
[4294696.754000] [fglrx] max single Inv  = 0
[4294696.754000] [fglrx] total      TIM  = 0
[4294871.453000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294871.453000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294871.453000] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of  chipset)
[4294871.453000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[4294871.460000] [fglrx] total      GART = 33554432
[4294871.460000] [fglrx] free       GART = 17559552
[4294871.460000] [fglrx] max single GART = 17559552
[4294871.460000] [fglrx] total      LFB  = 124436480
[4294871.460000] [fglrx] free       LFB  = 109076480
[4294871.460000] [fglrx] max single LFB  = 109076480
[4294871.460000] [fglrx] total      Inv  = 0
[4294871.460000] [fglrx] free       Inv  = 0
[4294871.460000] [fglrx] max single Inv  = 0
[4294871.460000] [fglrx] total      TIM  = 0
```

Am I warm?  Cold?  Getting warmer?  
Anyone?  Bueller?  ;-)

---

### Post by Ivhassel on 2006-06-08
**baldass_newbie**
First remove the fglrx from the repos, either from synaptic or by doing
```

sudo apt-get remove fglrx-kernel-source fglrx-control

```

I'm quite sure you're running an ATI **R2xx** chipset, so the latest driver version won't work.

Do this to verify what chipset you have:
```

lspci | grep ATI

```
Try my howto on how to get this fixed : [http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26)

---

### Post by DarthGroznii on 2006-06-09
Ivhassel -

I tried that method - all I got was a black screen for my trouble.  Furthermore, the package manager insisted on updating my old driver as soon as I managed to get the screen back up and running.

The only solution I can see is waiting for ATI to correct the problem, particularly their support for legacy Mobility Radeon cards, and then updating once they do.
 
In contrast - I put Dapper on my desktop machine, which has an NVidia card.  This was utterly painless.

Regards,

DarthGroznii

---

### Post by scxtt on 2006-06-09
i'm only able to use v. 8.24.8 in dapper (and breezy) w/ my X850Pro ... last night i tried to use the latest (following my 8.24.8 dapper install instructions (which work perfectly)) and after i was done [didn't get any errors during the process] - it was using the Mesa drivers ...

my conclusion, 8.25.? don't work well w/ the kernel that comes w/ dapper ...

i'll post my directions to see if they work for anyone else [keep in mind this ONLY works after a FRESH install of Dapper, there are too many overlaps taking a fglrx-enabled version of breezy and upgrading to dapper]:```
Method 2: Generating/Installing Ubuntu packages for the newer 8.24.8 drivers in Breezy Badger

Important Warning: Installation of this driver requires removing the restricted-modules package in order to work. That package includes drivers for madwifi (Atheros wireless cards), nvidia cards, and a handful of other devices. I provide a work-around for the madwifi drivers, but you need to perform it before removing the restricted modules (jump to end of this this post).

When running the dpkg-reconfigure command you should answer the questions that you know and take the defaults for the rest. You might want to say no to the monitor detection--it has caused X-Windows to crash for some people.

Remove existing fglrx driver

Remove Breezy's included drivers if they are installed:

       sudo apt-get remove xorg-driver-fglrx
       sudo apt-get remove fglrx-control
       sudo apt-get remove linux-restricted-modules-$(uname -r)
       sudo dpkg-reconfigure xserver-xorg #select the "ati" module

Reboot.

Installing the new driver

Download the ATI driver installer: 32bit Installer ([http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run](http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run))

This guide refers to the 32bit version of the driver. If you are using a x86_64 System you need the 64bit Installer. The installation procedure should be the same as for 32bit, except some filenames will differ slightly.

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

Install necessary tools:

       sudo apt-get install gcc-3.4 module-assistant build-essential
       sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

Create .deb packages:

       chmod +x ati-driver-installer-8.24.8-x86.run
       LANG=C LC_ALL=C ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/breezy

Install .deb packages:

       sudo dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb
       sudo dpkg -i fglrx-control_8.24.8-1_i386.deb
       sudo dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb

Remove any old fglrx deb's from /usr/src/:

       sudo rm /usr/src/fglrx-kernel*.deb

Compile the kernel driver:

       sudo module-assistant prepare
       sudo module-assistant update
       sudo module-assistant a-i fglrx

Update the xorg.conf file:

       sudo aticonfig --initial
       sudo aticonfig --overlay-type=Xv

Reboot.

Confirm that it worked

       $ fglrxinfo
       display: :0.0  screen: 0
       OpenGL vendor string: ATI Technologies Inc.
       OpenGL renderer string: RADEON 9700 Generic
       OpenGL version string: 2.0.5755 (8.24.8)
```

---

### Post by baldass_newbie on 2006-06-09
**Ivhassel**,

Was just going through it again (I'm a glutton for punishment) and I keep noticing this:

```

user@computer:~/ati$ sudo module-assistant build,install fglrx
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Done with /usr/src/fglrx-kernel-2.6.15-23-386_8.25.18-1+2.6.15-23.39_i386.deb .
Version 8.25.18-1+2.6.15-23.39 of fglrx-kernel-2.6.15-23-386 already installed, skipping.

```

Now, before you ask, I did run:

```
user@computer:~/ati$ sudo rm /usr/src/fglrx-kernel*.deb

```

with no errors.  And I also ran:

```
sudo apt-get remove fglrx-kernel-source fglrx-control
```

per your first line of instruction.  I'm wondering if I don't want to apt-get remove fglrx-kernel*?  

Anyway, pressing on.  I then run the following:

```
user@computer:~/ati$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

user@computer:~/ati$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-6

```

---

### Post by Ivhassel on 2006-06-09
[QUOTE=baldass_newbie]
<cut>

And I also ran:
```
sudo apt-get remove fglrx-kernel-source fglrx-control
```
per your first line of instruction.  I'm wondering if I don't want to apt-get remove fglrx-kernel*? 
[/quote]

Yes, I think so, no idea why I didn't mention that.

This might/should be correct:
```
sudo apt-get remove fglrx-kernel-source fglrx-control fglrx-kernel fglrx-kernel-`uname -r`
```
On a sidenote: I wouldn't advice removing packages with the use of wildcards (*), even though you get to answer (j/N), you could end up removing stuff you didn't want to.

Let me know if that works for you :)

---

### Post by baldass_newbie on 2006-06-09
I just posted to you in another thread.  Ignore that one and let me give this a shot.  
Thanks for your help.  It is appreciated.  
If we can crack this nut, lots of folks would be muy happy.  
Regards.

---

### Post by jinx099 on 2006-06-10
WTF???

Getting my fglrx driver to work in dapper was extremely easy!  Just type:

```
sudo apt-get install xorg-driver-fglrx xorg-driver-fglrx-dev
```

Then edit your xorg.conf file and change "ati" or "vesa" to fglrx... restart X and you're done!

I have an x800 GTO and now getting over 7000 FPS on glxgears.  Installed the Quake4 demo and it ran pretty well too.

EDIT:  Oh yeah, I think you need to enable all the sources that have been commented out first.

---

### Post by Ivhassel on 2006-06-10
[QUOTE=jinx099]WTF???

Getting my fglrx driver to work in dapper was extremely easy! [/QUOTE]

It is easy for recent cards. The drivers from the repos don't work with older cards, like mine, and like everyone's who posted here. Then it gets complicated.

---

