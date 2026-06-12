---
title: "ati drivers don't seem to work"
date: 2006-05-29
forum: Multimedia &amp; Video
---

### Post by tronica on 2006-05-29
I just install dapper and installed the ati drivers through synaptic. and I changed the xorg.conf, so that the driver read "fglrx". Then when i restarted x i did "fglrxinfo" and this is what i got.

> lyle@ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)



shouldn't that show my vid card? Plus all the windows seem jerky. I have a radeon 9550 and i have dual monitors setup. Heres my xorg.conf

> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "Default Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	Option         "Xinerama" "on"
	Option         "Clone" "off"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "CM2019"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor    "CM2019"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection



---

### Post by joshrobinson on 2006-05-29
yeah todays update for that package completely DESTROYED my dapper install

its totally useless right now

thank god i have my laptop to download a new daily iso of it.. hopefully it will work this time and not break itself

---

### Post by massivevoid on 2006-05-29
I have the problem, too. Hope they fix the problem soon. :(

---

### Post by joepotter on 2006-05-29
[QUOTE=joshrobinson]yeah todays update for that package completely DESTROYED my dapper install

its totally useless right now

thank god i have my laptop to download a new daily iso of it.. hopefully it will work this time and not break itself[/QUOTE]



Look guys; I know it is irritating when they break the X server in some way. I have a newer nVidia on-board card and it get borked by Ubuntu all the time.

But, when you get dumped into the command line just "nano /etc/X11/xorg.conf" and change the driver to "vesa" and reboot the x server. Or just reboot the computer.

Still an irritation to run a generic driver, yes! But it beats not running X at all, no?

On the other hand, I always keep another distro on the hard drive for bad days. A Breezy install would be good. :-)

---

### Post by joshrobinson on 2006-05-29
yeah but i ran Xgl, and now xgl wont work, especially with the vesa driver or ati driver

not to mention the new daily live cd wont install, because of some stupid error.. today has been a terrible day for me

---

### Post by Lovechild on 2006-05-29
That will be 5 hail Stallmans for using nonfree software and complaining that it broke your setup.

There is no way to ensure a working system when you don't have the ability to fix bugs. Sorry.

---

### Post by joshrobinson on 2006-05-29
[QUOTE=Lovechild]That will be 5 hail Stallmans for using nonfree software and complaining that it broke your setup.

There is no way to ensure a working system when you don't have the ability to fix bugs. Sorry.[/QUOTE]

shouldnt be in the repo's if it doesnt work.. thats all im saying

besides todays live cd is busted too, it wont install because of an error.. so im not complaining just about ATI.. just dapper in general today

---

### Post by Lovechild on 2006-05-29
[QUOTE=joshrobinson]shouldnt be in the repo's if it doesnt work.. thats all im saying

besides todays live cd is busted too, it wont install because of an error.. so im not complaining just about ATI.. just dapper in general today[/QUOTE]

You have my vote, I'm all for not having that kind of shit in the repos. It's only encouraging companies like ATI to not release specifications that we encourage the use of their closed drivers - longterm it serves to destablise the platform.. as you just discovered.

---

### Post by mlind on 2006-05-29
If I had a broken Ati install, I'd stop crying about it and revert to previous version.

---

### Post by djsroknrol on 2006-05-29
hey tronica....

fglrxinfo is saying that you're not running the right driver...mesa is wrong...brouse the forums for "fixing the mesa issue" in the tips and tricks section...I believe that's where I saw it.

I'm not running fglrx, but I try to keep up on ATI things...I have a 9200SE and run the Radeon OSS drivers...things are a little slow at times, but the eye candy works fine for me..

---

### Post by joshrobinson on 2006-05-29
[QUOTE=mlind]If I had a broken Ati install, I'd stop crying about it and revert to previous version.[/QUOTE]

i will when i get the time to reinstall dapper.. the package is broken it cant be removed, it cant be replaced at the moment.. its being a piece of crap.. so until i reinstall dapper i cant do anything about it

---

### Post by SymGeosis on 2006-05-30
Easy fix:

In a terminal ```
cd /var/cache/apt/archives
```
then:

```
sudo dpkg -i xorg-driver-fglrx_6.9.0-8.24.8+2.6.15.10-2_i386.deb
```

Restart X and enjoy the old ATI drivers. EDIT: You may need to reboot your computer.

---

### Post by wanger123 on 2006-05-30
If you're on a laptop don't bother trying to use the ATI drivers. You will have numerous fundamental problems with reboot, logout and shutdown, not to mention suspend/hibernate. I have reverted from fglrx back to ati until the issues are resolved (of course there is no 3d accel :evil: )

wanger123

---

### Post by musther on 2006-05-30
Anyone got any idea if this will be fixed before the release, it really should be.

---

### Post by st4rdr1ft3r on 2006-05-30
[QUOTE=tronica]I just install dapper and installed the ati drivers through synaptic. and I changed the xorg.conf, so that the driver read "fglrx". Then when i restarted x i did "fglrxinfo" and this is what i got.
> lyle@ubuntu:~$ fglrxinfo
Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

shouldn't that show my vid card? Plus all the windows seem jerky. I have a radeon 9550 and i have dual monitors setup. Heres my xorg.conf[/QUOTE]

I got this when I hadn't compiled the kernel module correctly ( I installed the drivers from ati's installer. ) check Xorg's log to see if it's loading.

---

### Post by bvanaerde on 2006-05-30
Like djsroknrol said, there's a whole thread about this:
[http://www.ubuntuforums.org/showthread.php?t=143283](http://www.ubuntuforums.org/showthread.php?t=143283)

It worked for me, so I guess it will work for you too.

---

### Post by luca.b on 2006-05-30
Check the logs for DRI initialization. If it is succesful and yet you have no acceleration, try symlinking /usr/lib/dri to /usr/X11R6/modules/dri. That fixed the problem for me.
And btw, that would that is ATI's driver to be broken, not Ubuntu's X.

---

### Post by musther on 2006-05-30
I've just tried 

```
sudo ln -s /usr/lib/dri/ /usr/lib/xorg/modules/dri
```

and now fglrxinfo output is:

```
musther@dominus:~$ fglrxinfo
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
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
[fglrx] API ERROR: could not register entrypoint for EnableVariantClientStateEXT
[fglrx] API ERROR: could not register entrypoint for DisableVariantClientStateEXT
[fglrx] API ERROR: could not register entrypoint for BindLightParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindMaterialParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTexGenParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTextureUnitParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindParameterEXT
[fglrx] API ERROR: could not register entrypoint for IsVariantEnabledEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantPointervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantBooleanvEXT[fglrx] API ERROR: could not register entrypoint for GetInvariantIntegervEXT[fglrx] API ERROR: could not register entrypoint for GetInvariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantFloatvEXT
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
[fglrx] API ERROR: could not register entrypoint for GetBufferParameterivARB[fglrx] API ERROR: could not register entrypoint for GetBufferPointervARB
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
[fglrx] API ERROR: could not register entrypoint for DisableVertexAttribArrayARB
[fglrx] API ERROR: could not register entrypoint for ProgramStringARB
[fglrx] API ERROR: could not register entrypoint for BindProgramARB
[fglrx] API ERROR: could not register entrypoint for DeleteProgramsARB
[fglrx] API ERROR: could not register entrypoint for GenProgramsARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvARB
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
[fglrx] API ERROR: could not register entrypoint for DeleteFragmentShaderATI[fglrx] API ERROR: could not register entrypoint for BeginFragmentShaderATI
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
[fglrx] API ERROR: could not register entrypoint for CurrentPaletteMatrixARB[fglrx] API ERROR: could not register entrypoint for MatrixIndexubvARB
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
[fglrx] API ERROR: could not register entrypoint for GenVisibilityQueriesATI[fglrx] API ERROR: could not register entrypoint for DeleteVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for BeginDefineVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndDefineVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for BeginUseVisibilityQueryATI
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
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterfvARB[fglrx] API ERROR: could not register entrypoint for GetObjectParameterivARB[fglrx] API ERROR: could not register entrypoint for GetInfoLogARB
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
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT
```

I've tried removing and reinstalling fglrx...

Oh, and I've removed the link, but it still happens...

---

### Post by st4rdr1ft3r on 2006-05-30
Do you think you could post your Xorg log please?

---

### Post by musther on 2006-05-30
Which bit, it's quite big.

---

### Post by poyner on 2006-05-30
my xserver seems to be stuffed as of the latest update too. bloody frustrating.... glxinfo is giving mesa no matter what i do. grrrr

---

### Post by musther on 2006-05-30
Ok, so here is my xorg log...

[http://www.flamingfatherland.org/jon/stuff/Xorg.0.log]("http://www.flamingfatherland.org/jon/stuff/Xorg.0.log")

---

### Post by francescob on 2006-05-30
[QUOTE=SymGeosis]Easy fix:

In a terminal ```
cd /var/cache/apt/archives
```
then:

```
sudo dpkg -i xorg-driver-fglrx_6.9.0-8.24.8+2.6.15.10-2_i386.deb
```

Restart X and enjoy the old ATI drivers. EDIT: You may need to reboot your computer.[/QUOTE]

hello
i've tried this but now my Xorg.log shows:

	warning	fglrx(0): Kernel Module version does *not* match driver.

	error	fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work

and fglrxinfo output is, of course, mesa

any hint?

francesco

---

### Post by st4rdr1ft3r on 2006-05-30
Well I couldn't see anything wrong with that, so I did abit of googling, and it seems that alot of people have been having trouble with the r2xx range.
One person got it working, but not properly by using libGL.so.1.2 from the old drivers.
Only thing I can suggest is to go back to using 8.24.08 drivers, ATI seem to be less than helpfull according to this:
[http://www.phoronix.com/?page=news_item&px=MTE2OA](http://www.phoronix.com/?page=news_item&px=MTE2OA)

---

### Post by st4rdr1ft3r on 2006-05-30
[QUOTE=francescob]warning	fglrx(0): Kernel Module version does *not* match driver.
	error	fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work[/QUOTE]

That suggests your still using the kernel module from 8.24.08, have you tried reinstalling linux-restricted-modules?

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]That suggests your still using the kernel module from 8.24.08, have you tried reinstalling linux-restricted-modules?[/QUOTE]

tried now, still no luck:

```
	information	fglrx(0): Kernel Module Version Information:

	information	fglrx(0):     Name: fglrx

	information	fglrx(0):     Version: 8.25.18

	information	fglrx(0):     Date: May 18 2006

	information	fglrx(0):     Desc: ATI FireGL DRM kernel module

	warning	fglrx(0): Kernel Module version does *not* match driver.

	error	fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
```

---

### Post by st4rdr1ft3r on 2006-05-30
hmmm, what does
```
apt-cache show xorg-driver-fglrx | grep Version
```

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]hmmm, what does
```
apt-cache show xorg-driver-fglrx | grep Version
```[/QUOTE]

```
sudo apt-cache show xorg-driver-fglrx | grep Version
Password:
Version: 7.0.0-8.25.18+2.6.15.11-1
Version: 6.9.0-8.24.8+2.6.15.10-2
```

the second is the one installed, in fact adept shows there's an update available

---

### Post by st4rdr1ft3r on 2006-05-30
thats the problem then, your trying to use 8.24.08 driver with the 8.25.18 module. just update the driver and it should work.

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]thats the problem then, your trying to use 8.24.08 driver with the 8.25.18 module. just update the driver and it should work.[/QUOTE]

but the new driver doesn't work with my graphic card (Xpress 200m), that's why i reverted to an older driver. What i have to do to use that?

---

### Post by st4rdr1ft3r on 2006-05-30
You'll need to use:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run)

and follow "Method 2" on

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I know it says for 8.25.18 but its the same process. That way you compile the 8.24.8 module back into the kernel, unless you can get the old restricted-modules back, but I'm not sure if you can do that.

---

### Post by bagofchickens on 2006-05-30
[QUOTE=Lovechild]..., I'm all for not having that kind of shit in the repos. It's only encouraging companies like ATI to not release specifications that we encourage the use of their closed drivers - longterm it serves to destablise the platform.. as you just discovered.[/QUOTE]

I completely agree. If the Ubuntu team had the ability to fix things, there would not be disasters like this happening. This morning a had a working Kubuntu system (with proprietary ati drivers for my 9250 graphics card), and after a regular update I had all kinds of trouble throughout most of the day, until I deinstalled linux-restricted -modules and xorg-driver-fglrx, and did a  sudo dpkg-reconfigure -phigh xserver-xorg (which brought back my desktop and allows me to play Quake 3). If stuff like this continues to happen, I am afraid I would be having shudders every time the little update notification icon appears in the system tray. Let ATI deal with their own part of the deal, and if they are not capable of supporting the products (even the older ones) we've paid for, there's always an alternative!

---

### Post by Colonel Kilkenny on 2006-05-30
Ok. I'll join the club again. I was proud when on Thursday driver from repository (8.24.08 ) worked as planned. Well, it isn't working anymore. Everything seems to be going ok, but for an example fglrxinfo gives this error:  "DDX driver fingerprint mismatch blahblah" and then says that Mesa is in use.

He ain't working, he's my Ati.

Edit. Got it solved. There was a some sort of a conflict between the old and the new driver. Now it's working (8.25.18 ) and for the first time the driver from repositories got upgraded almost without glitches.

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]You'll need to use:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run)

and follow "Method 2" on

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I know it says for 8.25.18 but its the same process. That way you compile the 8.24.8 module back into the kernel, unless you can get the old restricted-modules back, but I'm not sure if you can do that.[/QUOTE]

thanks! that worked, and now i have 3d again! unfortunately when i start XGL all freezes after a few seconds and i have to push the power button :(

---

### Post by st4rdr1ft3r on 2006-05-30
```
Option       "KernelModuleParm" "agplock=0"
```Make sure you have that in your xorg.conf. That should prevent the hardlocks.

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]```
Option       "KernelModuleParm" "agplock=0"
```Make sure you have that in your xorg.conf. That should prevent the hardlocks.[/QUOTE]

thank you again, your help is really priceless! now i have to get rid of a dri missing that appears when i try to run xgl :(

---

### Post by st4rdr1ft3r on 2006-05-30
I think that's normal. Not 100% on that though. But it comes up on mine and nothings wrong on it so I'm just ignoring it. Unless there's someone who can correct me?

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]I think that's normal. Not 100% on that though. But it comes up on mine and nothings wrong on it so I'm just ignoring it. Unless there's someone who can correct me?[/QUOTE]

seems like that it's causing compiz not to run. I'm not sure is that the problem by the way

i've this output:
```

/usr/local/bin/compiz.sh
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
FreeFontPath: FPE "/usr/lib/X11/fonts/misc/" refcount is 2, should be 1; fixing.
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1

```

the script contains:

```
#!/bin/sh
# Start up Xgl, compiz
# Run Xgl server on :1, on top of normal X
/usr/bin/Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
sleep 5
gnome-window-decorator &
compiz --replace gconf &
# Start KDE
exec startkde

```

but maybe we're going OT :)

---

### Post by st4rdr1ft3r on 2006-05-30
Does acceleration work when you just run normal Xorg?

---

### Post by francescob on 2006-05-30
yes, fglxgears runs

---

### Post by st4rdr1ft3r on 2006-05-30
Whats the output of fglrxinfo on both xorg and xgl?
I'll try and help you out when I get home (i'm about to leave work) which will be around 4.30ish. So if you post the information from fglrxinfo And also Xorg.log.0 and Xorg.log.93 (i think there should be a second one, although I can't remember for sure) then I'll check it out.

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]Whats the output of fglrxinfo on both xorg and xgl?
I'll try and help you out when I get home (i'm about to leave work) which will be around 4.30ish. So if you post the information from fglrxinfo And also Xorg.log.0 and Xorg.log.93 (i think there should be a second one, although I can't remember for sure) then I'll check it out.[/QUOTE]

on xorg i have: 
```
fra@francesco:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)
```

while on Xgl, running on display 1:

fra@francesco:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)

---

### Post by st4rdr1ft3r on 2006-05-30
Thats identical to what I have, how about /var/log/Xorg.0.log?

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]Thats identical to what I have, how about /var/log/Xorg.0.log?[/QUOTE]

Xorg.0.log:

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux francesco 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686

(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan 
[cut]
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
[cut]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.24.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) ATI Radeon/FireGL: The following chipsets are supported:
	[cut]
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.24.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.24g1                           
(II) ATI Proprietary Linux Driver Build Date: Apr 11 2006 13:36:57
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.24.1-driver-lnx-259766
(--) Chipset RADEON XPRESS 200M (RS480 5955) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[5] -1	0	0xb0209800 - 0xb02098ff (0x100) MX[B]
	[6] -1	0	0xb0209c00 - 0xb0209cff (0x100) MX[B]
	[7] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[8] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[9] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[10] -1	0	0xb0209000 - 0xb02097ff (0x800) MX[B]
	[11] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[12] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[13] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[14] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[15] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[16] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[17] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[18] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[24] -1	0	0x00008420 - 0x00008420 (0x1) IX[B]
	[25] -1	0	0x00008428 - 0x00008428 (0x1) IX[B]
	[26] -1	0	0x00008424 - 0x00008424 (0x1) IX[B]
	[27] -1	0	0x00008430 - 0x00008430 (0x1) IX[B]
	[28] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[29] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81db830
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[5] -1	0	0xb0209800 - 0xb02098ff (0x100) MX[B]
	[6] -1	0	0xb0209c00 - 0xb0209cff (0x100) MX[B]
	[7] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[8] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[9] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[10] -1	0	0xb0209000 - 0xb02097ff (0x800) MX[B]
	[11] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[12] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[13] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[14] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[15] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[16] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[17] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[18] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[26] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[27] -1	0	0x00008420 - 0x00008420 (0x1) IX[B]
	[28] -1	0	0x00008428 - 0x00008428 (0x1) IX[B]
	[29] -1	0	0x00008424 - 0x00008424 (0x1) IX[B]
	[30] -1	0	0x00008430 - 0x00008430 (0x1) IX[B]
	[31] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[32] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[33] 0	0	0xb01203b0 - 0xb01203bb (0xc) IS[B]
	[34] 0	0	0xb01203c0 - 0xb01203df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "KernelModuleParm" "agplock=0"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON XPRESS 200M (RS480 5955)" (Chipset = 0x5955)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x309b)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xb0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 262144 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON XPRESS 200M Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.24.8
	ABI class: X.Org Server Extension, version 0.2
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: AUO  Model: 3187  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 1
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 37  vert.: 23
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.610 redY: 0.350   greenX: 0.300 greenY: 0.560
(II) fglrx(0): blueX: 0.140 blueY: 0.140   whiteX: 0.320 whiteY: 0.330
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 96.3 MHz   Image Size:  367 x 230 mm
(II) fglrx(0): h_active: 1440  h_sync: 1504  h_sync_end 1536 h_blank_end 1760 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 906 v_blanking: 912 v_border: 0
(II) fglrx(0):  AUO
(II) fglrx(0):  B170PW03 V1
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay version 3.  2 power states available:
(II) fglrx(0):   1. 301/250MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 100/133MHz @ 60Hz []
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 16 modes found for primary display.
(--) fglrx(0): Virtual size is 1440x900 (pitch 1472)
(**) fglrx(0): *Mode "1440x900": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"   96.30  1440 1504 1536 1760  900 903 906 912
(**) fglrx(0): *Mode "1024x768": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   96.30  1024 1296 1328 1760  768 837 840 912
(**) fglrx(0): *Mode "800x600": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   96.30  800 1184 1216 1760  600 753 756 912
(**) fglrx(0): *Mode "640x480": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   96.30  640 1104 1136 1760  480 693 696 912
(**) fglrx(0):  Default mode "1280x800": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   96.30  1280 1424 1456 1760  800 853 856 912
(**) fglrx(0):  Default mode "1280x768": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   96.30  1280 1424 1456 1760  768 837 840 912
(**) fglrx(0):  Default mode "1152x864": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.30  1152 1360 1392 1760  864 885 888 912
(**) fglrx(0):  Default mode "848x480": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   96.30  848 1208 1240 1760  480 693 696 912
(**) fglrx(0):  Default mode "720x576": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   96.30  720 1144 1176 1760  576 741 744 912
(**) fglrx(0):  Default mode "720x480": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   96.30  720 1144 1176 1760  480 693 696 912
(**) fglrx(0):  Default mode "640x400": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   96.30  640 1104 1136 1760  400 653 656 912
(**) fglrx(0):  Default mode "640x350": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   96.30  640 1104 1136 1760  350 628 631 912
(**) fglrx(0):  Default mode "512x384": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   96.30  512 1040 1072 1760  384 645 648 912
(**) fglrx(0):  Default mode "400x300": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   96.30  400 984 1016 1760  150 753 756 912 doublescan
(**) fglrx(0):  Default mode "320x240": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   96.30  320 944 976 1760  120 693 696 912 doublescan
(**) fglrx(0):  Default mode "320x200": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   96.30  320 944 976 1760  100 653 656 912 doublescan
(--) fglrx(0): Display dimensions: (370, 230) mm
(--) fglrx(0): DPI set to (98, 99)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x000006ff
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): KernelModuleParm: "agplock=0"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xb0100000 - 0xb010ffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[7] -1	0	0xb0209800 - 0xb02098ff (0x100) MX[B]
	[8] -1	0	0xb0209c00 - 0xb0209cff (0x100) MX[B]
	[9] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[10] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[11] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[12] -1	0	0xb0209000 - 0xb02097ff (0x800) MX[B]
	[13] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[14] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[15] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[16] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[17] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[18] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[19] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[20] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[21] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[29] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[30] -1	0	0x00008420 - 0x00008420 (0x1) IX[B]
	[31] -1	0	0x00008428 - 0x00008428 (0x1) IX[B]
	[32] -1	0	0x00008424 - 0x00008424 (0x1) IX[B]
	[33] -1	0	0x00008430 - 0x00008430 (0x1) IX[B]
	[34] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[35] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[36] 0	0	0xb01203b0 - 0xb01203bb (0xc) IS[B]
	[37] 0	0	0xb01203c0 - 0xb01203df (0x20) IS[B]
(II) fglrx(0): UMM Bus area:     0xc0715000 (size=0x078db000)
(II) fglrx(0): UMM area:     0x38715000 (size=0x078db000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)

drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb6f55000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.24.8
(II) fglrx(0):     Date: Apr 11 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.15-23-k7
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [pcie] 65536 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x38000000 FBMappedSize: 0x00715000
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,1261)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 904)
(II) fglrx(0): Largest offscreen area available: 1472 x 349
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "UseFBDev" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		22 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): Interrupt handler installed at IRQ 201.
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "it"
(**) Generic Keyboard: XkbLayout: "it"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
AUDIT: Tue May 30 16:53:53 2006: 4933 X: client 9 rejected from local host
AUDIT: Tue May 30 16:54:12 2006: 4933 X: client 34 rejected from local host
AUDIT: Tue May 30 16:54:37 2006: 4933 X: client 9 rejected from local host
AUDIT: Tue May 30 16:54:44 2006: 4933 X: client 9 rejected from local host

```

---

### Post by st4rdr1ft3r on 2006-05-30
Is that when running Xorg or Xgl, if it's Xorg could you post one from Xgl as well. Also do you think you could post your xorg.conf please?

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]Is that when running Xorg or Xgl, if it's Xorg could you post one from Xgl as well. Also do you think you could post your xorg.conf please?[/QUOTE]

here is xorg.conf: ```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
	Option "KernelModuleParm" "agplock=0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

the log is (i think) from xorg session, but i've launched xgl and compiz through my script during this session

---

### Post by st4rdr1ft3r on 2006-05-30
Well for starters you should remove all the wacom stuff from xorg.conf (unless you have a graphics tablet ).

Also how are you launching xgl/compiz, is that script a .Xsession one?

I can't see anything wrong with xorg.conf, and according to the log everything is loading properly.

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]Well for starters you should remove all the wacom stuff from xorg.conf (unless you have a graphics tablet ).

Also how are you launching xgl/compiz, is that script a .Xsession one?

I can't see anything wrong with xorg.conf, and according to the log everything is loading properly.[/QUOTE]

xgl/compiz are launched from this script: 

```

#!/bin/sh
# Start up Xgl, compiz
# Run Xgl server on :1, on top of normal X
/usr/bin/Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
sleep 5
gnome-window-decorator &
compiz --replace gconf &
# Start KDE
exec startkde

```

called from this other file:
/usr/share/xsessions/compiz.desktop

[Desktop Entry]
Encoding=UTF-8
Name=Compiz
Comment=Candy store
Exec=/usr/local/bin/compiz.sh
Icon=
Type=Application

so i have a new session type in my login screen

also i have this
```

LD_PRELOAD=/usr/lib/libGL.so.1.2 /usr/bin/compiz

```
in
/etc/kde3/kdm/Xsetup


this worked flawlessy (except for windows decoration not showing) on this same machine but with dapper AMD64, now i've installed i386 for various reason and i have this problems. I'm pretty sure is compiz related

---

### Post by st4rdr1ft3r on 2006-05-30
I'd imagine so, since I don't see anything wrong.
what version of xgl/compiz are you using?

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]I'd imagine so, since I don't see anything wrong.
what version of xgl/compiz are you using?[/QUOTE]

latest downloaded from [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) repository
compiz is version 0.0.0.11
i've got also compiz-gnome and compiz-kde

---

### Post by st4rdr1ft3r on 2006-05-30
Ok, have you tried using the compiz-vanilla and compiz-vanilla-kde?
Might be worth a try.

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]Ok, have you tried using the compiz-vanilla and compiz-vanilla-kde?
Might be worth a try.[/QUOTE]

no luck even with vanilla...
compiz always says:

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1

---

### Post by st4rdr1ft3r on 2006-05-30
Hmmm.
I can't remember off the top of my head how to fix that. Best idea would be to search that error in the forums. I'm pretty sure I've fixed that error before and found the answer on here.
Sorry I can't be more help.

---

### Post by francescob on 2006-05-30
[QUOTE=st4rdr1ft3r]Hmmm.
I can't remember off the top of my head how to fix that. Best idea would be to search that error in the forums. I'm pretty sure I've fixed that error before and found the answer on here.
Sorry I can't be more help.[/QUOTE]

searched for "GLX_EXT_texture_from_pixmap" no results :(

---

### Post by Lil_Eagle on 2006-05-30
Sorry to butt in, but I just wanted to say that I have the fglrx driver working fine, although it still crashes my whole system if I switch back to X from a tty.  I was having problems seeing the splash during start and stopped and thought that was the ATI driver, but it turns out that was the lack of a VGA=791 instruction to the kernel.

I was having the same problem coming back from the tty with the old driver, so that isn't a help.  Vesa might work, haven't tried it yet (I would rather not have to revert).  I was thinking about trading the card in this machine for an older nvidia, but I see in the forums that people have almost just as much problem with those.  Since there are only two major video card companies now, and they both use propritary drivers, do we in the open source community really have a choice in the matter?  

I would love to find a card that just worked like it was supposed to.

FYI:

joe@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)

I really need to change the name of this machine.

---

### Post by st4rdr1ft3r on 2006-05-30
The driver is working fine now, its xgl/compiz thats busted.
But that can be a right pain getting working.

---

### Post by black hole sun on 2006-05-30
8.25 works fine for me

paul@nephilim:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 XT Generic
OpenGL version string: 2.0.5814 (8.25.18)

---

### Post by shiggs on 2006-05-30
[QUOTE=francescob]searched for "GLX_EXT_texture_from_pixmap" no results :([/QUOTE]


I am having the exact same problems as you, compiz (presumably) dies right after the script executs and I get windows with no borders stuck in the top left of screen. I guess because there is no window manager.

I am using the same (or similar) script to start compiz, I followed one of the ATI/XGL/Compiz howtos.

---

### Post by joshrobinson on 2006-05-30
[QUOTE=shiggs]I am having the exact same problems as you, compiz (presumably) dies right after the script executs and I get windows with no borders stuck in the top left of screen. I guess because there is no window manager.

I am using the same (or similar) script to start compiz, I followed one of the ATI/XGL/Compiz howtos.[/QUOTE]

if you type metacity --replace you will get the normal window borders back, so you dont have to logout and try your compiz commands again.. at least that will help you move around in xgl

---

### Post by shiggs on 2006-05-30
thanks for the tip.

I figured it out with the help of this [page]("http://micampe.it/2006/02/18/ubuntu-fglrx-xgl-compiz-and-missing-glx_ext_texture_from_pixmap") .

Before I found that I also switched gdm/xgl to run on display :0, but reinstalling the mesa libs and preloading it (in startcompiz script) did the trick.

---

### Post by phorque on 2006-05-30
Could somebody post the linux-restricted-modules and xorg-driver-fglrx debs that were just previous to the breakage? My archives have cleaned out the old ones and they aren't on the repos anymore. I have a Radeon 9200SE and am getting the "API" errors per Malone [#47371]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/47371")

---

### Post by jecos on 2006-05-30
So funny how many people can't just go around things.
If xorg-driver-fglrx won't uninstall then temporary move the file its complains it can't overwrite..  

:-D

---

### Post by phorque on 2006-05-31
Found a workaround here: [http://ubuntuforums.org/showthread.php?t=185033](http://ubuntuforums.org/showthread.php?t=185033)

---

### Post by JuddMaltin on 2006-06-02
I'm having a heck of a time getting the Mesa drivers to NOT show up when I load the fglrx drivers and the ATI drivers to show up.  There is a thread about this under "mesa issue", but it's a closed thread.  

I already did the kernel module uninstall reinstall, and linked the /usr/lib/xorg/xorg/modules/dri to /usr/lib/dri

link to /usr/lib/dri
```
judd@ludwig:/usr/lib/xorg/modules$ ls -la
total 4964
drwxr-xr-x 9 root root    4096 2006-06-02 00:29 .
drwxr-xr-x 3 root root    4096 2006-05-26 15:41 ..
lrwxrwxrwx 1 root root      13 2006-05-30 23:39 dri -> /usr/lib/dri/

```

contents of /usr/lib/dri
```
judd@ludwig:/usr/lib/dri$ ls -la
total 48572
drwxr-xr-x   2 root root    4096 2006-06-02 01:12 .
drwxr-xr-x 102 root root   40960 2006-06-02 01:13 ..
-rwxr-xr-x   1 root root 8591628 2006-06-02 01:12 atiogl_a_dri.so
lrwxrwxrwx   1 root root      13 2006-06-01 23:21 dri -> /usr/lib/dri/
-rw-r--r--   1 root root 2068744 2006-05-05 11:05 ffb_dri.so
-rwxr-xr-x   1 root root 8853148 2006-06-02 01:12 fglrx_dri.so
-rw-r--r--   1 root root 1974824 2006-05-05 11:05 i810_dri.so
-rw-r--r--   1 root root 1966664 2006-05-05 11:05 i830_dri.so
-rw-r--r--   1 root root 2056168 2006-05-05 11:05 i915_dri.so
-rw-r--r--   1 root root 2070504 2006-05-05 11:05 mach64_dri.so
-rw-r--r--   1 root root 2111016 2006-05-05 11:05 mga_dri.so
-rw-r--r--   1 root root 1962760 2006-05-05 11:05 r128_dri.so

```

My best guess is that my links really aren't correct.  Which are the proper fglrx libs that /usr/lib/libGL* should be pointing to, exactly?

My card via lspci:
```
0000:03:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
0000:03:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)

```

output of fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

All the flgrx associated files.  Which ones should I link to the /usr/lib/libGL* ?  Or should I?

```
judd@ludwig:~$ cat locate_fglrx
/var/lib/dpkg/info/xorg-driver-fglrx.preinst
/var/lib/dpkg/info/xorg-driver-fglrx.list
/var/lib/dpkg/info/xorg-driver-fglrx.postrm
/var/lib/dpkg/info/xorg-driver-fglrx.shlibs
/var/lib/dpkg/info/xorg-driver-fglrx.md5sums
/var/lib/dpkg/info/fglrx-control.md5sums
/var/lib/dpkg/info/fglrx-control.list
/var/cache/apt/archives/fglrx-kernel-source_8.24.8+2.6.15.10-2_i386.deb
/var/cache/apt/archives/xorg-driver-fglrx_6.9.0-8.24.8+2.6.15.10-2_i386.deb
/var/cache/apt/archives/fglrx-control_8.24.8+2.6.15.10-2_i386.deb
/var/cache/apt/archives/fglrx-kernel-source_8.25.18+2.6.15.11-1_i386.deb
/var/cache/apt/archives/xorg-driver-fglrx_7.0.0-8.25.18+2.6.15.11-1_i386.deb
/var/cache/apt/archives/fglrx-control_8.25.18+2.6.15.11-1_i386.deb
/lib/linux-restricted-modules/2.6.15-23-k7/fglrx
/lib/linux-restricted-modules/2.6.15-23-k7/fglrx/libfglrx_ip.a.GCC4
/lib/linux-restricted-modules/2.6.15-23-k7/fglrx/firegl_public.o
/lib/linux-restricted-modules/2.6.15-23-k7/fglrx/fglrx.mod.o
/lib/linux-restricted-modules/2.6.15-23-386/fglrx
/lib/linux-restricted-modules/2.6.15-23-386/fglrx/libfglrx_ip.a.GCC4
/lib/linux-restricted-modules/2.6.15-23-386/fglrx/firegl_public.o
/lib/linux-restricted-modules/2.6.15-23-386/fglrx/fglrx.mod.o
/usr/share/doc/xorg-driver-fglrx
/usr/share/doc/xorg-driver-fglrx/changelog.Debian.gz
/usr/share/doc/xorg-driver-fglrx/copyright
/usr/share/doc/fglrx-control
/usr/share/doc/fglrx-control/changelog.Debian.gz
/usr/share/doc/fglrx-control/copyright
/usr/bin/fglrx_xgamma
/usr/bin/fglrxinfo
/usr/lib/xorg/modules/linux/libfglrxdrm.so
/usr/lib/xorg/modules/drivers/fglrx_drv.so
/usr/lib/dri/fglrx_dri.so
/usr/lib/fglrx
/usr/lib/fglrx/libGL.so.1.xlibmesa
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/lib/libfglrx_gamma.so.1.0
/usr/lib/libfglrx_dm.so.1.0
/usr/lib/libfglrx_pp.so.1.0
/usr/lib/libfglrx_dm.so.1
/usr/lib/libfglrx_pp.so.1
/usr/lib/libfglrx_gamma.so.1
/usr/X11R6/lib/fglrx
/home/judd/strace_fglrx
```

And these are the existing links.  Notice that libGL.so.1.2 is dated today, which is what I installed, the fglrx stuff.  But libGLU.so.1 is dated 05-05.  That seems like the wrong thing.  Should I worry about libGLU
```
judd@ludwig:~$ ls -la /usr/lib/libGL*
lrwxrwxrwx 1 root root     12 2006-06-02 01:13 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rwxr-xr-x 1 root root 642476 2006-06-02 01:12 /usr/lib/libGL.so.1.2
lrwxrwxrwx 1 root root     20 2006-05-26 20:09 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.060401
-rw-r--r-- 1 root root 479244 2006-05-05 11:05 /usr/lib/libGLU.so.1.3.060401

```

Help.  I'm totally obsessed.  Is this card not supported by the ATI drivers?  There is NOTHING in the Xorg logs that would help :( :(

---

### Post by Xanatos Craven on 2006-06-02
I have read just about everything having to do with ati driver troubleshooting on this forum, and probably as much as I can ingest from the 'net as a whole before my eyes melt out of my skull. In the amount of time that I have wasted in trying to get this stupid video card to work on different distributions, I could have been building a 50ft eiffel tower of paper clips or curing cancer!

I'm sorry, but to require this much troubleshooting and command-line fiddling just to get 3D screensavers that don't freeze up or are horribly sluggish, is totally inexcusable, ATI. If it was a game-specific problem, I would've understood, but... no, just no. I give up, it's time for a new card. <_<

---

