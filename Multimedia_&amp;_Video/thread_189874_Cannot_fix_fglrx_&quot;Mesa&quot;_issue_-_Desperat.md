---
title: "Cannot fix fglrx &quot;Mesa&quot; issue - Desperate"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by ipaidforthisname on 2006-06-05
I didn't want to start a new thread on this, as there have been quite a few, but I am beyond desperate. 

My problem is the “Fglrx Mesa” issue. All my applications run sluggishly (scrolling, etc), and I can't get any 3d support. I have an ATI Mobility 9800 in a Dell Inspiron 9100. My fglrx drivers worked fine in Breezy Badger. 

I have tried every step outlined in the “Howto: Fixing the “Mesa Issue” to no avail. I have tried installing the FGLRX drivers via different means (making the debs, and using repos, etc). I have even tried three different versions of the FGLRX drivers that I scoured the internet for. I don't appear to have the problem of the DRI lib file not being found, so creating a symlink does nothing. I have also tried using a different libGL.so.1.2 file, but that has done nothing. 

Here is my FGLRXINFO output:

```

julian@julian-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

flgl_glxgears outputs this error:
```

julian@julian-laptop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30

```


I am not totally sure what that “XFree86-DRI" missing on display” error is, but it goes away if I change drivers, or if I revert back to a stock xorg.conf file (I am pretty sure), but it always outputs Mesa for all values.


Attached is my xorg.conf and Xorg.0.log

This is pretty frustrating. I don't know what else to do. It wouldn't be an issue if normal applications didn't run like such crap. Scrolling through image galleries in Firefox or Opera is painful, to say the least.

---

### Post by ipaidforthisname on 2006-06-05
Here is my Xorg.0.log

[www.bluewavestudios.com/basenotes/ipaid/Xorg.0.log.txt](www.bluewavestudios.com/basenotes/ipaid/Xorg.0.log.txt)

---

### Post by deadgobby on 2006-06-05
Hi,
 I read this ditty on Distro watch.
[COLOR="Red"]I reported this bug and received a polite response from the developers. While waiting for a fix, I've found a reasonable workaround. I edited file /etc/X11/xorg.conf and replaced the "ati" driver with "vesa". The vesa driver works with just about any hardware, but it's a noticeably slow driver. I no longer experience crashes, but I can forget about playing PlanetPenguin-Racer (ppracer, formerly known as TuxRacer).[/COLOR]

---

### Post by sparhawk on 2006-06-05
I have been getting the same errors but without the
"Xlib:  extension "XFree86-DRI" missing on display ":0.0" "
part.

cassie@gorn:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I have followed the instructions on [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

several times and same thing. 

cassie@gorn:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  33
  Current serial number in output stream:  33

I even get this

cassie@gorn:~$ dmesg | grep fglrx
[4294700.143000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294700.145000] [fglrx] Maximum main memory to use for locked dma buffers: 429 MBytes.
[4294700.145000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294701.295000] [fglrx] total      GART = 67108864
[4294701.295000] [fglrx] free       GART = 51118080
[4294701.295000] [fglrx] max single GART = 51118080
[4294701.295000] [fglrx] total      LFB  = 126808064
[4294701.295000] [fglrx] free       LFB  = 116322304
[4294701.295000] [fglrx] max single LFB  = 116322304
[4294701.295000] [fglrx] total      Inv  = 0
[4294701.295000] [fglrx] free       Inv  = 0
[4294701.295000] [fglrx] max single Inv  = 0
[4294701.295000] [fglrx] total      TIM  = 0

If anyone knows what may be the issue please help. I had the same issue in breezy and now dapper. If there is any other info that could help let me know.

---

### Post by lexxonnet on 2006-06-05
try running sudo aticonfig --initial, after installing the fglrx driver... it might automatically fix up things....

---

### Post by KiLLeR_WoMBaT on 2006-06-05
I swear I've tried every tip, trick and how-to on these forums and for some reason I still cannot get the ATI driver to work.  I can't get DRI with the stock dapper driver either.

I have an ATI Radeon 9600 Mobility.  It worked great with Breezy just installing the official ATI drivers.  Not so here.  Everything seems to install fine...no errors.  Upon reboot I get TWO drum sounds at the login screen and after putting in the user name and password...nothing.  Just a blank brown screen and my mouse cursor.  I have to ctrl-alt-bkspc to get back to the login screen and login in with a failsafe terminal session.  Here I have to dpkg-reconfigure xserver-xorg to use vesa.  Upon reboot I get the desktop...but still MESA!!!!!

This is driving me nuts!  Any help?  xorg.conf looks stock and normal compared to others posted that work with the ATI drivers.

---

### Post by sparhawk on 2006-06-06
[QUOTE=lexxonnet]try running sudo aticonfig --initial, after installing the fglrx driver... it might automatically fix up things....[/QUOTE]


I have tried running aticonfig --initial, it changes the xorg.conf driver to fglrx but still no go... any other ideas?

---

### Post by MrSiegal on 2006-06-06
I'm getting the exact same problem on my laptop with mt ATI Mobility Radeon 9700 Pro.

---

### Post by jk_warrior on 2006-06-06
I have this very same problem!

I hope there is someone who knows a solution!

---

### Post by Lil_Eagle on 2006-06-06
I managed to get the drivers to work (sort of).

After the aticonfig --initial, you need another command.  That is:

aticonfig --overlay-type=Xv

Hope that helps.

My machine will now shut down and reboot OK (although I had to also change a line in /boot/grub/menu.lst so that it passes vga=791 to the kernel, otherwise I don't see the boot messages.

The only problem I am running into now (and it is very frustrating) is that when I open a vitual terminal, when I press <CTRL><ALT><F7> to go back to X, my system freezes.

I tried this with kdm, gdm, gnome and KDE (all combinations) but same results.

It's either this or poor performance using vesa drivers.  Hopefully ATI will fix this bug (it is a bug).  I really hate proprietary drivers!  What can we do?  All the cards nowadays are either ATI or nVidia, and both are proprietary.

---

### Post by tomski on 2006-06-06
i have a similar problem even though i have been a bit lazy.

i was running breezy with fglrx & all was fine up until the upgrade to the dapper beta thats when the problems started at first when i run:
flgrxinfo 
i had the output for the 'mesa' driver:

```
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

so i thought ..well this is to be expected as i have just upgrded to a 'beta' version!
 so i sat back and patiently waited for the bug to be fixed in time for the stable release. 
Now i took this approach to avoid repeatedly trying to fix the same problem when i upgraded again before the stable version was release(i hate flogging dead horses!!)
I continued to wait for a month or so updating & upgrading all the time with no 3d but a fully working desktop now i'm here & willing to try to fix my problem, which the errors for have changed slightly because when i run:

fglrxinfo

i get this error:

```
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

now as i mentioned i have not changed a single conf, the only time flgrx has been touched is via apt-get upgrade which also may have installed various versions of restricted modules or when i ran update-manager -d to get to dapper from breezy 

here is the untouched xorg.conf that worked in breezy


```

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
	Option	    "XkbVariant" "pc"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Emulate3Buttons" "false"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Buttons" "7"
	Option	    "ButtonMapping" "1 2 3 6 7"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver      "fglrx"
	VideoRam    131072
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```


do any of you guys have some pointers or should i just wade my way through all the other fglrx issue threads to find the answer??



i have tried to uninstall the resticted modules and driver & reinstall them with the first reinstall being the resticted modules followed by the xorg driver but it still gives the same error

---

### Post by tomski on 2006-06-06
here is my Xorg.0.log its in a zip as it was too big to upload as text and too long to post?????[ATTACH]10727[/ATTACH]

---

### Post by sparhawk on 2006-06-06
[QUOTE=Lil_Eagle]I managed to get the drivers to work (sort of).

After the aticonfig --initial, you need another command.  That is:

aticonfig --overlay-type=Xv

Hope that helps.

My machine will now shut down and reboot OK (although I had to also change a line in /boot/grub/menu.lst so that it passes vga=791 to the kernel, otherwise I don't see the boot messages.

The only problem I am running into now (and it is very frustrating) is that when I open a vitual terminal, when I press <CTRL><ALT><F7> to go back to X, my system freezes.

I tried this with kdm, gdm, gnome and KDE (all combinations) but same results.

It's either this or poor performance using vesa drivers.  Hopefully ATI will fix this bug (it is a bug).  I really hate proprietary drivers!  What can we do?  All the cards nowadays are either ATI or nVidia, and both are proprietary.[/QUOTE]


I tried that too but still nothing. I guess it will just have to stay with XP until Edgy. Maybe ATI will work then. Odd that it worked in breezy.

---

### Post by lexxonnet on 2006-06-07
I cant for the life of me understand why it wont work :S
It seems fine on my machine, and I'm running a 9600Pro.

Did you guys install linux-restricted-modules? Which processor architecture are you running btw?

---

### Post by lucascr on 2006-06-07
Hello, maybe my experience may help someone.
I upgraded from breezy to dapper on my Asus laptop (A4759GLH P4 3.2G, 512M RAM, scheda video ATI MOBILITY RADEON 9700 PRO 64 MB) and I get some problems using the ubuntu dapper's driver: no 3D accelleration (as in Breezy), no hibernate (but I had in breezy) and the video fan always running (a very annoying problem not present in breezy).
Following the the guide at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") I have been able to stop the fan and get hibernate working, but I still have non 3D accelleration:
```

> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```
One thing I noticed is that in /etc/X11/xorg.conf I have:
```

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	VideoRam    64000
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

```
Why there are two devices? And why the first has "ati" instead of "fglrx"?

Overall I solved the two main problems, so I could say to be happy for now. :) 
Ciao,
Luca

---

### Post by sparhawk on 2006-06-07
[QUOTE=lexxonnet]I cant for the life of me understand why it wont work :S
It seems fine on my machine, and I'm running a 9600Pro.

Did you guys install linux-restricted-modules? Which processor architecture are you running btw?[/QUOTE]

I followed the guide everyone has been mentioning on here and it does say to install the linux-restricted-modules so yes I have. I am running a p4 if the helps and the vid card is a "ati X300 PCIE"

---

### Post by Lil_Eagle on 2006-06-07
I've got a P4 2.53Ghz, ATI 9800 Pro.

I'm pretty sure the problem lies with Xorg 7.0.  I heard that it was buggy, and that's why gentoo still uses 6.9 (so did breezy).  I don't know how to downgrade since I am not that good with Linux yet.  I was thinking of messing around with Gentoo because I would learn a lot in the process.  That's one disadvantage with Ubuntu is that for the most part "it just works". 

It's the problems that happen that teach you the most about how things work, and installing Gentoo is a problem, thus a good learning experience.  The problem is that I need to have another PC to do it on, as I'm not about to risk this one in such an endeavor.  My wife already is upset that I am in the middle of installing this or that on this PC and she can't use the internet.

I have tried fixing this problem by changing display managers, from gdm to kdm, but both do the same.  I tried the older fglrx drivers, same problem.  Therefore to me it has to be xorg.

---

### Post by sidefx on 2006-06-07
P4 2.8GHz with a 9800pro and I'm having the exact same problem. I hadn't even noticed it today until I got transparency running in enlightenment and it all ran insanely slow. fglrxinfo shows it's using mesa. I've tried all the suggestions above to no avail. 

lexxonnet: perhaps you could post your xorg.conf??

---

### Post by sidefx on 2006-06-07
hrm... well, I managed to get back to the fglrx drivers. I'm not sure which of the two changes I made fixed it, but perhaps one of them will help one of you?  I made the following changes to xorg.conf

changed driver to be "fglrx" everywhere (before one was fglrx and one ati):

```

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9800 XT (RV350 NJ)"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

```

commented out the composite extension (which I had added to get the transparency):

```

Section "Extensions"
#	Option	    "Composite" "true"
EndSection

```

So, I guess maybe you can't use composite with hardware acceleration or something? :-/

---

### Post by sparhawk on 2006-06-08
[QUOTE=sidefx]hrm... well, I managed to get back to the fglrx drivers. I'm not sure which of the two changes I made fixed it, but perhaps one of them will help one of you?  I made the following changes to xorg.conf

changed driver to be "fglrx" everywhere (before one was fglrx and one ati):
[/QUOTE]


Nope that didn't work... still get the same

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

here is my xorg.conf if it helps anyone figure it out but seems ok to me

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
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

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Dell E193FP"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Driver      "fglrx"
	VideoRam    128000
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor    "Dell E193FP"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
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

### Post by sparhawk on 2006-06-08
OK I have just fixed all of my issues

cassie@gorn:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

The new ATI drivers do support xorg 7

I just went to there site and looked at the instructions for the installed package and ran it and poof everything works. Here is the link to the instructions.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.25.18-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.25.18-inst.html)

And here is a link to the driver for x86

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

Remember to download the installer package and not the ones compiled for xFREE86 or XORG 6.8

Let me know how it goes for you guys and if I can help I will.

Later :)

---

### Post by DonQuixote on 2006-06-08
Did you do the "automatic", "custom", or "distibution specific" installation?

My laptop has:
ATI 9600 Radeon Mobility graphics card,
linux-image-686,
fresh install of Dapper.

I'm going to try it, once again.
>takes a deep breath<

---

### Post by DonQuixote on 2006-06-08
Alright, first thing I notice is that in the instructions it says:

> # POSIX Shared Memory (/dev/shm) support is required for 3D apps
# glibc version 2.2 or 2.3
# Linux kernel 2.4 or higher
# XOrg 6.7 or 6.8; XFree86 version 4.1, 4.2, or 4.3

According to the installer, I have glib2.1 which is NOT a version that the instructions say is required.  Now, in looking for glibc2.2 in Synaptic, I found this, libg++2.8.1.3-glibc2.2.  So, I installed it, and then ran the ATI installer again.  Again, it told me that I only had glib2.1.

Could this be at least one problem for the installation, and where would you get glibc2.2?

---

### Post by scxtt on 2006-06-09
sparhawk, how many Frames Per Second are you getting when you run fglrx_glxgears?

i'm curious if there's any performance benefit to 8.25.? ...

---

### Post by sidefx on 2006-06-09
Great news sparhawk, just about to try it myself. Just curious, but if you enable the composite extension in your xorf.conf file, does everything keep working?  I'd love to get some proper transparency going without all the hassle of glx.


EDIT: bah, disregard that. According to fglrxinfo I'm already running 8.25.18 - and it was installed direct from the ubuntu repos I think...

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 XT Generic
OpenGL version string: 2.0.5814 (8.25.18)

and enabling the composite extension causes my system to go back to mesa.

---

### Post by sparhawk on 2006-06-09
[QUOTE=scxtt]sparhawk, how many Frames Per Second are you getting when you run fglrx_glxgears?

i'm curious if there's any performance benefit to 8.25.? ...[/QUOTE]

Depends on the size of the window. Here is my output from running it. I am just glad that the screensavers are rendered now. I don't play any 3d games so I don't know if this is good or not. You tell me.

cassie@gorn:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
934 frames in 5.0 seconds = 186.800 FPS
1074 frames in 5.0 seconds = 214.800 FPS
2390 frames in 5.0 seconds = 478.000 FPS
2481 frames in 5.0 seconds = 496.200 FPS
2480 frames in 5.0 seconds = 496.000 FPS
2484 frames in 5.0 seconds = 496.800 FPS
2469 frames in 5.0 seconds = 493.800 FPS
2484 frames in 5.0 seconds = 496.800 FPS
1568 frames in 5.0 seconds = 313.600 FPS
4756 frames in 5.0 seconds = 951.200 FPS
3853 frames in 5.0 seconds = 770.600 FPS
2159 frames in 5.0 seconds = 431.800 FPS
2191 frames in 5.0 seconds = 438.200 FPS
2517 frames in 5.0 seconds = 503.400 FPS
3567 frames in 5.0 seconds = 713.400 FPS
3538 frames in 5.0 seconds = 707.600 FPS

and if you know of any 3d games native to linux let me know. I have a hard time finding any quality ones.

---

### Post by MrSiegal on 2006-06-10
I got mine working again. The problem seems to be with the updating system. I reinstalled Dapper from scratch with an install-cd without any problems. Ok, no problems other that having to reinstall every program I had previously installed...

---

### Post by scxtt on 2006-06-10
[QUOTE=sparhawk]Depends on the size of the window. Here is my output from running it. I am just glad that the screensavers are rendered now. I don't play any 3d games so I don't know if this is good or not. You tell me.
[snip]
and if you know of any 3d games native to linux let me know. I have a hard time finding any quality ones.[/QUOTE]i would have just left it @ the size it is after you start it from the terminal ... here's what i get:```
$hostname [~]
:> fgl_glxgears
Using GLX_SGIX_pbuffer
5904 frames in 5.0 seconds = 1180.800 FPS
6307 frames in 5.0 seconds = 1261.400 FPS
6353 frames in 5.0 seconds = 1270.600 FPS
6319 frames in 5.0 seconds = 1263.800 FPS
6345 frames in 5.0 seconds = 1269.000 FPS
$hostname [~]
```i ran Quake4 in linux w/ pretty good results ...

---

### Post by Jeff59 on 2006-06-10
I have the same problem with ati 9100 runing on a HP.  Does anyone know is this a UBUNTU problem or an ATI.  I'm thinking of trying another distro.  I love UBUNTU but video is a mager need.

---

### Post by ipaidforthisname on 2006-06-10
I worked on this issue for the entire day **solid**. It was awful.

I think I finally figured it out, though. I managed to get it fixed, but I ran into some xorg issues after I did get it fixed. 

I am almost 1000% sure it's an ATI issue. The reason being, I finally gave up today and decided I needed to go back to Breezy. The awful sluggishness was infuriating me. When I finally got Breezy all setup, I installed the fglrx 8.25 drivers, and bam, I was hit with the Mesa problem. I decided to try older drives, and still all I could get was Mesa and a sluggish OS. 

I booted into windows to finally give up on Ubuntu totally. I was spent. I finally realized that the only thing that could be causing the problems are the new 8.25 drivers. I did everything I could to try and get rid of them, but for some odd reason, it would not work. I reinstalled Breezy again, and installed the 8.24.8 drivers, and it worked flawlessly, just like it did before.

I started thinking that it might work if I reinstalled dapper, and didn't even touch the 8.25 drivers, but instead installed the older 8.24 drivers. I tried it, and it worked. I had perfect 3d acceleration in Dapper. The next problem I ran into was with Xorg. Whenever I enabled Xinerama(sp?), it would revert back to Mesa. I needed my dual monitor setup, and could not figure out how to get dual monitors without it reverting right back to Mesa. 

I concluded **that** was an Xorg issue, because I am in Breezy with dual monitors and Xinerama with perfect 3d acceleration. 

I think there is something fundamentally wrong with the latest ATI Fglrx drivers.

---

### Post by Trurl on 2006-06-10
[QUOTE=sparhawk]

The new ATI drivers do support xorg 7

I just went to there site and looked at the instructions for the installed package and ran it and poof everything works. Here is the link to the instructions.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.25.18-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.25.18-inst.html)

And here is a link to the driver for x86

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

Remember to download the installer package and not the ones compiled for xFREE86 or XORG 6.8
[/QUOTE]

I just tried these and the instructions are for a ...i386.run file while the download is for an x86.run file. I modified the instructions to fit the x86 file but I still have the mesa problem.  What do you mean by the "installer package," and where can I get it? 

Thanks,

Trurl

---

### Post by sparhawk on 2006-06-11
When you go to the download page it lists the the different packages. One is labled "ATI Driver Installer".

---

### Post by eMcJagger on 2006-06-16
Hello,

Like apparently many people, I have been having great trouble getting the ATI graphics card in my Toshiba laptop to work properly in Dapper, though it seemed to work fine on Breezy.  I have checked many many forums and HOWTOs, starting with [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide), but nothing works.


MAIN PROBLEM:

3d graphics seem to be okay; screensavers work, as does the openGL 3d viewport of my 3d animation application (Houdini).  Currently fgl_glxgears doesn't work (see below), but it has worked at various stages of my fruitless fix attempts.  One problem is that in Houdini and some other apps (eg. Cinelerra), parts of the UI are black.  This wouldn't be so bad, but also, at random but frequent occasions while I'm interacting with the UI, the screen will just go black, then go to text-only login, and then go to a black screen with "_" at the top, at which point I have to manually turn the machine off.  So I'm thinking the problem is with the 2d, not 3d, aspect of the drivers, if that's possible.

When I follow the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide), I don't notice any errors, but after rebooting, fglrxinfo still says I'm using mesa3d, not ati (see below).  Even after trying all the other tips I could find, I can never get fglrxinfo to show that I'm using ati.

Note that Houdini didn't work properly right away with Breezy but the problem was different; crazy triangular drawing artifacts all over the place instead of black and crashes.  I fixed that by following the Breezy instructions here:  [https://wiki.kubuntu.org/BinaryDriverHowto/ATI](https://wiki.kubuntu.org/BinaryDriverHowto/ATI).

Sorry to post a problem so similar to so many others out there, but I'm really at my wit's end.  Note (in case you haven't already) that though I've been using Linux for a couple years, I'm not very savvy with sys-admin stuff.  That's mainly why I've so loved Ubuntu -- very friendly to the non-technical.  But I'm stuck.  Any help much, much appreciated.


SYSTEM INFO:

Here is a bunch of info about my system that people seemed to find relevant on the forums I've checked.  Let me know if you need more.


**********************************


Graphics card:

ATI Mobility Radeon 9000

Laptop model:

Toshiba Satellite A70


**********************************


Output from lsmod | grep fglrx:

fglrx                 391756  8
agpgart                36784  2 fglrx,ati_agp


**********************************


Output from dmesg | grep fglrx:

[4294697.374000] [fglrx] Maximum main memory to use for locked dma buffers: 372 MBytes.
[4294697.374000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294716.316000] [fglrx:firegl_init_mask_ram] *ERROR* maskram_type not detected
[4294716.317000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294716.317000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294716.317000] [fglrx] AGP detected, AgpState   = 0x1f00021b (hardware caps of chipset)
[4294716.318000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[4294716.336000] [fglrx] total      GART = 33554432
[4294716.336000] [fglrx] free       GART = 17559552
[4294716.336000] [fglrx] max single GART = 17559552
[4294716.336000] [fglrx] total      LFB  = 60911616
[4294716.336000] [fglrx] free       LFB  = 52719616
[4294716.337000] [fglrx] max single LFB  = 52719616
[4294716.337000] [fglrx] total      Inv  = 0
[4294716.337000] [fglrx] free       Inv  = 0
[4294716.337000] [fglrx] max single Inv  = 0
[4294716.337000] [fglrx] total      TIM  = 0


**********************************


Output from fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


**********************************


Output from fgl_glxgears:

Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  33
  Current serial number in output stream:  33


**********************************


I have attempted to attach my xorg.conf file.  Hopefully it worked!

---

### Post by Coda on 2006-06-16
I just noticed this problem tonight, and fixed it in 15 minutes. I hope you all are having the same problem, because otherwise it sounds *really* hard to fix.

I hadn't installed the right meta-packages, and so my restricted modules were out of sync with the new kernel they just pushed out (2.6.15-23 instead of 2.6.15-25). Installing linux-686 *and* linux-restricted-modules-686 did it for me, and presumably I'll get the restricted modules for the next kernel they release.

If that doesn't work, best of luck!

---

### Post by sparhawk on 2006-06-17
[QUOTE=Coda]I just noticed this problem tonight, and fixed it in 15 minutes. I hope you all are having the same problem, because otherwise it sounds *really* hard to fix.

I hadn't installed the right meta-packages, and so my restricted modules were out of sync with the new kernel they just pushed out (2.6.15-23 instead of 2.6.15-25). Installing linux-686 *and* linux-restricted-modules-686 did it for me, and presumably I'll get the restricted modules for the next kernel they release.

If that doesn't work, best of luck![/QUOTE]


He is right. Everyone that has fixed there problem will have to update their restricted modules. The new kernel the pushed out was 2.6.15-25 but the restricted modules you were using are for 2.6.15.23. It sucks that this happens but it does. Just enter:

[COLOR="Red"]sudo apt-get update linux-restricted-modules-[/COLOR][COLOR="RoyalBlue"]686[/COLOR] 

and that should update the modules for you. Remember to change the "[COLOR="RoyalBlue"]686[/COLOR]" to what you are running. After that reboot and all should work... hopefully :S

---

### Post by Galban on 2006-06-17
Ok people, read this. Whats giving you the Mesa problem on fglrxinfo it's a Mesa vesion of libGL.1.2.so. You guys, you have to remplace it with a Ati's version of it, that's it. What are you gonna lose trying this? --> 

[http://www.ubuntuforums.org/showthread.php?t=197471](http://www.ubuntuforums.org/showthread.php?t=197471)

Good Luck!

---

### Post by eMcJagger on 2006-06-17
Thanks for the replies folks; my hope is renewed.  Still some issues though:

Sparhawk, I'm trying your method.  First of all -- again, pardon my ignorance -- I just want to confirm that, since synaptic says linux-386 is installed and linux-686 is not, I should change the "686" to "386" in the command you gave, right?  (By the way, I have a pentium4 -- should I be running 686?)

In any case, when I type:

sudo apt-get update linux-restricted-modules-386 

I get:

E: The update command takes no arguments

Perhaps you meant "install" instead of "update"?  Anyway, I tried to install linux-restricted-modules-386 with synaptic, but I got an error saying it depends on linux-restricted-modules-2.6.15-25-386, and when it try to install that it says it depends on linux-image-2.6.15-25-386, which does not appear in my list of packages -- I only have linux-image-2.6.15-23-386.  It says both the installed version and the latest version are 2.6.15-23.39.  How do I get linux-image-2.6.15-25-686?

Thanks again -- your help is much appreciated.

---

### Post by eMcJagger on 2006-06-17
Shoot, I meant "How do I get linux-image-2.6.15-25-386?", not "686" -- sorry.

---

### Post by Galban on 2006-06-17
First of all, you need to know wich kernel are you using... do this to know it:

```
ls /boot/
```

So then, install corresponding restricted modules. By the way, the kernel in the Dapper's repositories has been upgrade from 2.6.15-23 to 2.6.15-25. So there is nothing wrong to go with last one, and yes, sub-version 686 is perfectly adecuate for your Pentium IV, and 386 will do the job too. Choose one!

---

### Post by eMcJagger on 2006-06-18
Okay, I've figured out how to install linux-restricted-modules-386 -- I had to edit either the Ubuntu 6.06 LTS Security Updates or just Updates channel (can't remember which one) in Synaptic's repositories list and check on the "Officially Supported" checkbox, which was off for some reason.  So now linux-restricted-modules-386 appears in the package list and I installed it, but the I still get the same results:  buggy Houdini graphics with frequent crashes, fgl_glxgears gives the same errors, and still mesa instead of ati in the output of fglrxinfo.  I've tried rebooting, redoing the steps outlined in [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide) and [https://wiki.kubuntu.org/BinaryDriverHowto/ATI](https://wiki.kubuntu.org/BinaryDriverHowto/ATI) as well as Galban's link, [http://www.ubuntuforums.org/showthread.php?t=197471](http://www.ubuntuforums.org/showthread.php?t=197471), all to no avail.  All my system info is the same as given in my previous post, except I now get this from dmesg | grep fglrx:

[17179601.764000] [fglrx] Maximum main memory to use for locked dma buffers: 372 MBytes.
[17179601.764000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179619.064000] [fglrx:firegl_init_mask_ram] *ERROR* maskram_type not detected
[17179619.064000] [fglrx] AGP detected, AgpState   = 0x1f00021b (hardware caps of chipset)
[17179619.064000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[17179619.080000] [fglrx] total      GART = 33554432
[17179619.080000] [fglrx] free       GART = 17559552
[17179619.080000] [fglrx] max single GART = 17559552
[17179619.080000] [fglrx] total      LFB  = 60911616
[17179619.080000] [fglrx] free       LFB  = 52719616
[17179619.080000] [fglrx] max single LFB  = 52719616
[17179619.080000] [fglrx] total      Inv  = 0
[17179619.080000] [fglrx] free       Inv  = 0
[17179619.080000] [fglrx] max single Inv  = 0
[17179619.080000] [fglrx] total      TIM  = 0


Any ideas?  I'm beginning to despair...

---

### Post by sparhawk on 2006-06-18
Did you try going to ATI's website and running their installer?

---

### Post by eMcJagger on 2006-06-19
Firstly, sparhawk, yes, I have tried installing the drivers from ati's website several times, and it has never yet worked.  Last time I tried, I noticed these errors when uninstalling the driver (before re-installing) by typing "sudo sh ./fglrx-uninstall.sh" in the download directory:

```

/usr/share/fglrx/./postun_drv.sh: line 167: [: too many arguments
/usr/share/fglrx/./postun_drv.sh: line 174: [: too many arguments
/usr/share/fglrx/./postun_drv.sh: line 179: [: too many arguments
expr: syntax error
expr: syntax error
sed: -e expression #1, char 4: unexpected `,'
sed: -e expression #1, char 1: unknown command: `,'
restore of system environment completed
Uninstall fglrx driver complete...

```


Don't know if that means anything to anyone.


[QUOTE=Galban]First of all, you need to know wich kernel are you using... do this to know it:

```
ls /boot/
```

So then, install corresponding restricted modules. By the way, the kernel in the Dapper's repositories has been upgrade from 2.6.15-23 to 2.6.15-25. So there is nothing wrong to go with last one, and yes, sub-version 686 is perfectly adecuate for your Pentium IV, and 386 will do the job too. Choose one![/QUOTE]

Galban, in desperation, I installed linux-686 linux-restricted-modules-686 in *addition* to linux-386 and linux-restricted-modules-386 -- I hope that's not a bad thing to do, Synaptic didn't complain.  Here's the output from "ls -1 /boot/" (-1 for clarity) before and after Installing linux-686 -- I'm not quite sure how to figure out what my kernel is from it:

BEFORE linux-686 INSTALL:
```

abi-2.6.12-10-386
abi-2.6.12-10-686
abi-2.6.12-9-386
abi-2.6.15-23-386
abi-2.6.15-23-686
abi-2.6.15-25-386
abi-2.6.15-25-686
config-2.6.10-5-386
config-2.6.10-6-386
config-2.6.12-10-386
config-2.6.12-10-686
config-2.6.12-50preempt
config-2.6.12-9-386
config-2.6.15-23-386
config-2.6.15-23-686
config-2.6.15-25-386
config-2.6.15-25-686
grub
initrd.img-2.6.10-5-386
initrd.img-2.6.10-6-386
initrd.img-2.6.12-10-386
initrd.img-2.6.12-10-686
initrd.img-2.6.12-50preempt
initrd.img-2.6.12-9-386
initrd.img-2.6.15-23-386
initrd.img-2.6.15-23-686
initrd.img-2.6.15-25-386
initrd.img-2.6.15-25-686
memtest86+.bin
System.map-2.6.10-5-386
System.map-2.6.10-6-386
System.map-2.6.12-10-386
System.map-2.6.12-10-686
System.map-2.6.12-50preempt
System.map-2.6.12-9-386
System.map-2.6.15-23-386
System.map-2.6.15-23-686
System.map-2.6.15-25-386
System.map-2.6.15-25-686
vmlinuz-2.6.10-5-386
vmlinuz-2.6.10-6-386
vmlinuz-2.6.12-10-386
vmlinuz-2.6.12-10-686
vmlinuz-2.6.12-50preempt
vmlinuz-2.6.12-9-386
vmlinuz-2.6.15-23-386
vmlinuz-2.6.15-23-686
vmlinuz-2.6.15-25-386
vmlinuz-2.6.15-25-686

```

AFTER linux-686 INSTALL:
```

abi-2.6.12-10-386
abi-2.6.12-10-686
abi-2.6.12-9-386
abi-2.6.15-23-386
abi-2.6.15-23-686
config-2.6.10-5-386
config-2.6.10-6-386
config-2.6.12-10-386
config-2.6.12-10-686
config-2.6.12-50preempt
config-2.6.12-9-386
config-2.6.15-23-386
config-2.6.15-23-686
grub
initrd.img-2.6.10-5-386
initrd.img-2.6.10-6-386
initrd.img-2.6.12-10-386
initrd.img-2.6.12-10-686
initrd.img-2.6.12-50preempt
initrd.img-2.6.12-9-386
initrd.img-2.6.15-23-386
initrd.img-2.6.15-23-686
memtest86+.bin
System.map-2.6.10-5-386
System.map-2.6.10-6-386
System.map-2.6.12-10-386
System.map-2.6.12-10-686
System.map-2.6.12-50preempt
System.map-2.6.12-9-386
System.map-2.6.15-23-386
System.map-2.6.15-23-686
vmlinuz-2.6.10-5-386
vmlinuz-2.6.10-6-386
vmlinuz-2.6.12-10-386
vmlinuz-2.6.12-10-686
vmlinuz-2.6.12-50preempt
vmlinuz-2.6.12-9-386
vmlinuz-2.6.15-23-386
vmlinuz-2.6.15-23-686

```


Also, for all of the following packages, synaptic says the installed version *and* the latest version are 2.6.15.23:

linux-386
linux-686
linux-image-386
linux-image-686
linux-restricted-modules-386
linux-restricted-modules-686

Sparhawk says that linux-restricted-modules-686 should be version 2.6.15.*25*, but my system doesn't seem to have access to this latest version.  Are my repositories not configured right?  Here's my /etc/apt/souces.list:

```

deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

# ADDED BY ME
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper main universe multiverse restricted

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

```


Curiously, linux-restricted-modules-**2.6.15-25**-686 linux-restricted-modules-**2.6.15-25**-686 are also installed, and synaptic says the installed and latest version of both of these is 2.6.15.11-2.  I don't understand the relationship between the 2.6.15-25 in the name and the 2.6.15.11-2 of the version.  For other packages, these two strings are more similar -- for example, linux-image**-2.6.15-25**-386 and linux-image-**2.6.15-25**-686 are version 2.6.15-25.43.


One final thing:  When I run the check.sh script provided by the ati website (either with or without sudo), I get this:

```
=====================================================================
 ATI Technologies
=====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

```

I tried to switch to a console by doing ctrl-alt-F1, but it didn't work.  Neither did running "sudo init 3".  Niether method gave me errors, they just had absolutely no effect.  I know the ctrl-alt-F1 thing used to work -- I imagine I've broken it with all my inexpert driver hacking.


Thanks again for all your continuing help, everybody.  Hopefully we'll figure it out eventually...

---

### Post by sparhawk on 2006-06-19
try running this at the command line to find your kernel version.

[COLOR="Red"]uname -r[/COLOR]

that should at least let you know what linux-restricted-modules you need.

You should get 2.6.15-25 and either 386 or 686... if not check you repositories and see if they have the official sites so that you can upgrade your kernel to the newest one

---

### Post by eMcJagger on 2006-06-19
uname -r gives me 2.6.15-25-686, but synaptic still says that the installed and latest version of linux-restricted modules-686 is 2.6.15.23.  Shouldn't it be 2.6.15.25?

---

### Post by Tosa on 2006-06-20
Hi all,

I've got the same Mesa problem on my Athlon XT/Radeon 9600 XT Pc. It was fglrx drivers before kernel update two days ago...

My kernel is reported as 2.6.15-25-386, but restricted modules are 2.6.15-23. When I tried to upgrade them the message was that I've already got the latest ones!

Since I have an Athlon, maybe I should Install k7 kernel? If I do, should I just install k7 modules in adept, or there is more to it?

Another thing: in my xorg.conf there are thre instances of Device

```
Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BoardName   "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
 # 
	Identifier  "device1"
	Driver      "fglrx"
	BoardName   "ati"
	BusID       "PCI:2:0:0"
	Screen      1
EndSection
```

Should all of them be there?

---

### Post by Tosa on 2006-06-21
So I did install k7 kernel, hoping that it would solve Mesa problem. It didn't though. When I booted in previous kernel (the one before 2.6.15-25) I didn't have fglrx any more, but Mesa. So I figured that xorg.conf was to blame. I reverted to the oldest file I had and fglrx showed up. Here is my current xorg.conf, maybe it would be of some use to some one.

```
Section "Monitor"
	Identifier   "SyncMaster"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

---

### Post by eMcJagger on 2006-06-22
EPILOGUE:

Hi everyone.

Just wanted to let y'all know what eventually happened to my sorry case (switch from Breezy to Dapper killed ati graphics, esp. on Houdini 3d animation package).

So, after about 10 days of caca Houdini graphics + fruitless toil, I finally decided give up on Dapper, backup my /home and reinstall Ubuntu 5.10 from scratch, wiping out my hard drive.  The re-install went super smoothly (after I figured out how to properly burn the .iso to disk).  I found I that I had those crazy triangular artifacts all over the place in Houdini, which I expected 'cause that's what I had originally in 5.10.  However, when I followed the 5.10 instructions at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), which had originally quickly fixed the problem, I found it didn't work this time.  I can't remember the details of my tumultuous progress through that long, dark night, but I tried all sorts of configurations with 'sudo dpkg-reconfigure xserver-xorg', and direct hacks to '/etc/X11/xorg.conf', and rebooted more than 30 times (I know 'cause it did the integrity check), and got a variety of artifact including bad screen aspect ratio/resolution, black windows, and system freezes.  Then, in a desperate attempt to just try everything, I removed all things fglrx with synaptic, restored the xorg.conf file that the install originally provided, and rebooted -- and to my joy/confusion/slight irritation, Houdini worked beautifully!  

It seems that the solution was to leave the fglrx stuff out of the equation altogether and just use the original (open source, I think?) "ati" driver.  I don't understand why it didn't work from the getgo when I reinstalled Breezy, though -- perhaps I accidentally knocked something into place through my inexpert hacking around, but I doubt if I'll ever know what it was.  So now I'm back were I was 1.5 weeks ago, a little older, a little cleaner, a little bitter-er, perhaps marginallly wiser.  A pity I can't upgrade to Dapper -- maybe if I did upgrade and used this original xorg.conf file it would work, but I'm much too terrified to try.  Oh well, Breezy still kicks ***.  I might get a new desktop soon; I'll be sure to get an nVidia card, which, I understand, is much more Linux-friendly.

Thanks for all your feedback, folks.  Below is my current, happy xorg.conf file:

```
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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
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
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
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

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	#Option	    "VideoOverlay" "on"
	#Option	    "OpenGLOverlay" "off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by BuffaloX on 2006-06-22
I hope that everybody dosn't switch to Linux tomorrow.
I have one ATI card to get rid of first. :rolleyes:
In my oppinion this is ATIs fault 100%, and this is second time they let me down.
First time was with the MACH32 card which **NEVER** got to work in Windows.

---

### Post by mrbrdo on 2006-09-23
ipaidforthisname: it is reported that most probably fglrx will not work if you enable dual monitors. Also, note, in newer xorg, Composite is enabled by default, if it is not explicitly disabled in xorg.conf.
To fix, add this at the end of xorg.conf:
```
Section "Extensions"
   Option "Composite" "disable"
EndSection
```

---

### Post by vinx on 2006-10-07
Take a look at [http://www.thinkwiki.org/wiki/Problems_with_fglrx](http://www.thinkwiki.org/wiki/Problems_with_fglrx) where I found my fix:

>     (WW) fglrx(0): Kernel Module version does *not* match driver. 
    (EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work 

The cause for this trouble might be that there resist multiple versions of the fglrx module within the kernel module search path.
Go to /lib/modules/<your linux kernel version>/ and type # grep fglrx modules.dep.
If grep finds multiple lines you nailed down the problem. All you have to do now is to delete any versions of the module (look at the filedate) but the most current one. Then run # depmod and you are done.

---

