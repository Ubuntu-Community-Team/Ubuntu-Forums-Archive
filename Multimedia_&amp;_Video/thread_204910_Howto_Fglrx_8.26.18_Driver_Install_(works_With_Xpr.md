---
title: "Howto: Fglrx 8.26.18 Driver Install (works With Xpress Series Cards Now!)"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by fitzman49 on 2006-06-27
Finally ATI released the much anticipated update to the fglrx driver which now has support for xorg 7.0 and works with all xseries cards.  Mine (xpress 200m) did not work with the fglrx 8.25.18 drivers but now have full support and 3D acceleration.  These drivers also address the black screen hanging issue when xorg is shutdown or restarted.  Heres a quick tutorial on how I got it working.  Much thanks to IVHassel for the tutoiral before that I used to get the old drivers working.:) 

Cards that are known to work with these new drivers can be found here: [https://www2.ati.com/drivers/linux/linux_8.26.18.html]("https://www2.ati.com/drivers/linux/linux_8.26.18.html")


Installing the new driver

Download the ATI driver installer from the ATI Website: 32bit Installer:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run]("https://www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run")

**Edit:**64 bit users:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run]("https://www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run")

**Edit:**New 8.27.10 drivers are now available.  Follow the guide but change the file names accordingly.

32 Bit: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run]("https://www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run")

64 Bit:[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.27.10-x86_64.run]("https://www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.27.10-x86_64.run")

This guide refers to the 32bit version of the driver. If you are using a x86_64 System you need the 64bit Installer. The installation procedure should be the same as for 32bit, except some filenames will differ slightly.

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

Install necessary tools:
```
sudo apt-get update 
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```



Create .deb packages:

```
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
```


Install .deb packages:

```
sudo dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb 
sudo dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb 
sudo dpkg -i fglrx-control_8.26.18-1_i386.deb
```


Remove any old fglrx deb's from /usr/src/:

```
sudo rm /usr/src/fglrx-kernel*.deb
```


Compile the kernel module:

Code:

```
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```


Note: You have to recompile the kernel module after each kernel update!

Update the xorg.conf file:

```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
```


Reboot.

Confirm that it worked


```
[fitzy@greenmachine49]~ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series Generic
OpenGL version string: 2.0.5879 (8.26.18)
```




If you have any questions feel free to post here or private message me and I will try to help as best as possible.\\:D/

---

### Post by jecos on 2006-06-27
Make sure you blacklist fglrx in /etc/default/linux-restricted-modules-common, since the majority will have restricted-modules installed..

---

### Post by soongwoo on 2006-06-27
A thread says
 - I have to blacklist fglrx before installing latest ati driver.
 - After installation. fglrx should not be blacklisted.

But, the above procedure by fitzman49 does not mention blacklisting fglrx module. What is correct procedure?

 1) blacklist fglrx by editing /etc/default/linux-restricted-modules-common:
      DISABLED_MODULES="fglrx"
 2) follow the steps as fitzman49 and reboot
 3) NOT blacklist fglrx by editing /etc/default/linux-restricted-modules-common:
      DISABLED_MODULES=""

Is it the right procedures to install latest ATI driver?

Thanks
soongwoo

---

### Post by Rojahon on 2006-06-27
[QUOTE=soongwoo]A thread says
 - I have to blacklist fglrx before installing latest ati driver.
 - After installation. fglrx should not be blacklisted.

But, the above procedure by fitzman49 does not mention blacklisting fglrx module. What is correct procedure?

 1) blacklist fglrx by editing /etc/default/linux-restricted-modules-common:
      DISABLED_MODULES="fglrx"
 2) follow the steps as fitzman49 and reboot
 3) NOT blacklist fglrx by editing /etc/default/linux-restricted-modules-common:
      DISABLED_MODULES=""

Is it the right procedures to install latest ATI driver?

Thanks
soongwoo[/QUOTE]
yeah, I'm confused on this too.  Any help?

---

### Post by whatever on 2006-06-28
ok, you obviously know how to copy&paste.
why not just link to [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually) ?

---

### Post by syxbit on 2006-06-28
i already installed the ati drivers from the Ubuntu repository. (obviously the older ones)
do i have to uninstall them first, and if so, how ?
thanks

---

### Post by soongwoo on 2006-06-28
I did follow the steps from 1) to 3).
But, 1) and 3) are not necessary, I think.
The procedure by fitzman49 is fine.

soongwoo

---

### Post by Knight on 2006-06-28
I just installed the new drivers and am having the same problems as with the 8.25. Input seems to lag (noticably worse with higher resolutions) in games both native, and through wine/cedega. Also, cedega seems to fail me at the "3d acceleration" test about 30% of the time (instead of passing me 10% of the time with 8.25). While fgl_glxgears gives about the same FPS as 8.25, glxgears has improved by about 100fps. Anyone know how to increase FPS and fix the input lag issue? The PC in question is [this one]("http://www.comparestoreprices.co.uk/laptops/fujitsu-siemens-amilo-a1650.asp"). Thanks in advance.

---

### Post by flapane on 2006-06-28
I CANNOT compile using this method, see the link [http://pastebin.ca/73772](http://pastebin.ca/73772)

I have my headers installed, but I get this damned error

---

### Post by DiamondX on 2006-06-28
I followed the instructions exactly, including the blacklisting, but when I do fglrxinfo, I get this:
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

I have a Radeon 9200.

Edit: Fixed the [C0DE] tags.

---

### Post by mvaranda on 2006-06-28
I have followed this procedure without any problem. However, after reboot I get:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

my lspci shows: 0000:01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobi lity T2] (rev 80)

my /etc/X11/xorg.conf is like:

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
#	Identifier "Default Screen"

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
	Load  "dri"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. M10 NT [FireGL Mobility T2]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "ATI Technologies, Inc. M10 NT [FireGL Mobility T2]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
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

### Post by herrdoktor330 on 2006-06-28
I just wanted to say that this fixed all my problems. Good lord. Now everything works like it's supposed to. I think linux is starting to warm up to me... with the help of you people.

Thank you, Thank you, Thank you. The original thread post worked for me fine as stated.

- herrdoktor330

---

### Post by Rojahon on 2006-06-28
[QUOTE=mvaranda]I have followed this procedure without any problem. However, after reboot I get:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
[/QUOTE]

I'm having the same problem.  I'm running an Xpress 200M like the author.

---

### Post by syxbit on 2006-06-28
so, anyone know about how to go about uninstalling the fglrx drivers installed from repo's ?

---

### Post by bvchurch on 2006-06-28
I am having one heck of a time getting something going here and I don't think it is the ATI Driver but instead something to do with OpenGL.

First quick specifications:
Athlon 64 3200, K8NS Ultra 939, ATI X800XLAIW, Ubuntu 6.06 Dapper x86_64

Okay then a copy of the important part of xorg.conf
```
[SIZE="2"]
Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 86.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. R420 JK [Radeon X800]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. R420 JK [Radeon X800]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
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
[/SIZE]
```

When I run fglrxinfo
$ fglrxinfo
Error: couldn't find RGB GLX visual!

When I run glxgears
$ glxgears
Error: couldn't get an RGB, Double-buffered visual


Any help would be much appreciated.

EDIT I did notice under the first section I changed the driver from "ati" to "fglrx".  Rebooted, same issue.

And now I think the problem may be with the monitor section, the horizon and vertical frequencies i entered from the manual.  THe monitor i am using on this machine is a KDS XFlat XF9S.

---

### Post by shakespeare on 2006-06-28
Thanks, this works fine for me. Benchmark using glxgears increased from <200 to >2200, and now [3ddesktop]("http://ubuntuforums.org/showthread.php?t=100169") works.
Ubuntu Dapper on Sony Vaio VGN-A117S with ATI Mobility Radeon 9700.

---

### Post by Centaur5 on 2006-06-28
I have an hp pavilion ze2000 that has the ATI 200M video card and I got a problem while running the command sudo module-assistant build,install fglrx:

dh_testroot
 &#9474; rm -f configure-stamp                                                      &#9618;
 &#9474; rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a                               &#9618;
 &#9474; rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd                        &#9618;
 &#9474; rm -rf .tmp_versions                                                       &#9618;
 &#9474; rm -rf patch                                                               &#9618;
 &#9474; dh_clean                                                                   &#9618;
 &#9474; rm /usr/src/modules/fglrx/debian/control                                   &#9618;
 &#9474; rm /usr/src/modules/fglrx/debian/dirs                                      &#9618;
 &#9474; if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \           &#9618;
 &#9474;         cat /usr/src/modules/fglrx/debian/control.template >               &#9618;
 &#9474; /usr/src/modules/fglrx/debian/control; \                                   &#9618;
 &#9474;         fi                                                                 &#9618;
 &#9474; if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \                   &#9618;
 &#9474;         mv /usr/src/modules/fglrx/debian/postinst

---

### Post by hashstat on 2006-06-28
[QUOTE=syxbit]so, anyone know about how to go about uninstalling the fglrx drivers installed from repo's ?[/QUOTE]

You should be able to just click the *xorg-driver-fglrx* entry in Synaptic, select "Mark for Removal," and then click Apply. Or...

```
apt-get remove xorg-driver-fglrx
```

You may want to change the driver in your xorg.conf file back to *ati* so that X will work while your getting the new driver working.

By the way, I was able to get the 8.26.18 driver to work on my Dell D810 laptop (ATI Mobility Radeon X600) with the big desktop accross two external monitors connected through a docking station (taking a breath...), where the previous version failed.  All I did was download the installer from ATI and follow the instructions.  Just run the installer, which throws up a graphical wizard, and do all the default actions.

```
sudo sh ati-driver-installer-8.26.18-x86.run
```

The installer installs an uninstaller for uninstalling the driver (say that ten times fast).  It is found at */usr/share/fglrx/fglrx-uninstall.sh*.  Easy.

Now if I could only get Xgl/compiz working. ;)

Best of luck!

---

### Post by EReckase on 2006-06-28
OK, I followed the normal procedure for installing these drivers - it hasn't changed much since the 8.24.8 ones.  I have an HP Pavilion dv8000, AMD64 processor with the 200M Radeon Xpress.  I'm working with a 32-bin installation of Dapper.

Everything looks until right at the end...the screen blanks as usual after when the boot process is nearly complete, but instead of a login screen, I get zilch, nada, just a black screen.  There are no errors to speak of in the Xorg log file, and my system log seems to think that the screen should be working dandy...but there's just nothing there.  I'll be happy to post any log information that folks request, but I don't think it'll help much.

I've reverted to 8.24.8 without difficulty, and they work nicely.  For those with the 200M cards that get the 8.26.18 drivers to work - what's the glxgears framerate now?  Any better?

---

### Post by graigsmith on 2006-06-28
i just tried out the drivers, got it working. but if you click new user, it just hardlocks. and you have to reset your computer.  :roll: @ ati
mabey they will get it working before this card is obsolete.  na probably not.  i should probably sell this and get an nvidia card.

---

### Post by MAO on 2006-06-29
** My Note (HP nx 6125 / AMD Turion 64/ATI 200/1GB) still works VEry slow !!!**

My settings:

oem@JAN:/var/log$ fgl_glxgears
Using GLX_SGIX_pbuffer
198 frames in 5.0 seconds = 39.600 FPS
221 frames in 5.0 seconds = 44.200 FPS
213 frames in 5.0 seconds = 42.600 FPS
215 frames in 5.0 seconds = 43.000 FPS
212 frames in 5.0 seconds = 42.400 FPS
213 frames in 5.0 seconds = 42.600 FPS
220 frames in 5.0 seconds = 44.000 FPS
218 frames in 5.0 seconds = 43.600 FPS
218 frames in 5.0 seconds = 43.600 FPS
215 frames in 5.0 seconds = 43.000 FPS
219 frames in 5.0 seconds = 43.800 FPS
217 frames in 5.0 seconds = 43.400 FPS
216 frames in 5.0 seconds = 43.200 FPS
214 frames in 5.0 seconds = 42.800 FPS
213 frames in 5.0 seconds = 42.600 FPS
217 frames in 5.0 seconds = 43.400 FPS
221 frames in 5.0 seconds = 44.200 FPS
214 frames in 5.0 seconds = 42.800 FPS
221 frames in 5.0 seconds = 44.200 FPS
197 frames in 5.0 seconds = 39.400 FPS

oem@JAN:/var/log$

__________________________________________________________________________
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
	Option		"XkbLayout"	"us"
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

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
	Option		"NoDDC"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName" "ATI Proprietary Driver"
	Option		"MadelName" "Generic AutoDetecting Monitor"
	Option		"DPMS" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Viewport	0 0
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
______________________________________________________________________

oem@JAN:/var/log$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5879 (8.26.18)

oem@JAN:/var/log$

______________________________________________________________________

oem@JAN:~$ dmesg | grep fglrx
[17179618.980000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179618.992000] [fglrx] Maximum main memory to use for locked dma buffers: 804 MBytes.
[17179618.996000] [fglrx] module loaded - fglrx 8.26.18 [Jun 22 2006] on minor 0[17179623.712000] [fglrx] total      GART = 134217728
[17179623.712000] [fglrx] free       GART = 118226944
[17179623.712000] [fglrx] max single GART = 118226944
[17179623.712000] [fglrx] total      LFB  = 126038016
[17179623.716000] [fglrx] free       LFB  = 114143232
[17179623.716000] [fglrx] max single LFB  = 114143232
[17179623.716000] [fglrx] total      Inv  = 0
[17179623.716000] [fglrx] free       Inv  = 0
[17179623.716000] [fglrx] max single Inv  = 0
[17179623.720000] [fglrx] total      TIM  = 0
________________________________________________________________________

I do not know what exacly you need to HELP me and give all information I have .
Pleace show me the way to corect configure!!!!!!

[IMG]http://diesel-i.elcat.kg/uploads/post-2650-1151571438.png[/IMG]

---

### Post by DarthGroznii on 2006-06-29
These instructions simply did not yield a result to me - I have an HP Compaq nx7000 laptop with an ATI Mobility Radeon 9200 (64 MB).

I followed the procedure, no errors.  Reboot and it hangs with a black screen.  

This is just how it was with the set previous to this one.

I am using the "ati" driver instead of the "fglrx" one for the moment, but this is extremely irritating as fglrx used to work when I was on Breezy.

---

### Post by flapane on 2006-06-29
[QUOTE=flapane]I CANNOT compile using this method, see the link [http://pastebin.ca/73772](http://pastebin.ca/73772)

I have my headers installed, but I get this damned error[/QUOTE]

bump

---

### Post by rbZ on 2006-06-29
Hi. I installed the drivers on my radeon 9100, but fglrxinfo gives me this: 

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

and dmesg | grep fglrx this: 

$ dmesg | grep fglrx
[4294684.598000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294684.598000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[4294684.598000] [fglrx] module loaded - fglrx 8.26.18 [Jun 22 2006] on minor 0
[4294697.171000] Modules linked in: i82365 rsrc_nonstatic pcmcia_core ipv6 af_packet nls_cp437 ntfs md dm_mod fglrx agpgart psmouse mousedev parport_pc lp parport ext3 jbd thermal processor fan usbhid forcedeth ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk ide_generic sata_nv libata scsi_mod amd74xx ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
[4294708.263000] [fglrx] Internal AGP is not supported in 2.6 kernel.
[4294708.263000] [fglrx:firegl_unlock] *ERROR* Process 4289 using kernel context 0

---

### Post by eschatron on 2006-06-29
So, when is this likely to make it into the official repos?  I'm not a big fan of compiling my own drivers.

---

### Post by Rojahon on 2006-06-29
[QUOTE=rbZ]Hi. I installed the drivers on my radeon 9100, but fglrxinfo gives me this: 

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
[/QUOTE]

I have the same problem with my 200M.  Is there a setting somewhere I'm missing?  I looked in my xorg file and there is nothing about mesa.

---

### Post by TD-Linux on 2006-06-29
I followed your instructions the first time, but I messed up and forgot to install the *.deb's :P

The second time, when I got to installing the *.debs, the first one (the xorg one) gives me an error copying libGL.so.1.2. It appears that it detected that it was a diversion, and tried to move it to a backup directory, but libGL.so.1.2 was there also. Should I remove libGL.so.1.2 from that directory, or what?

I think I have the official Ubuntu fglrx packages installed also. Maybe it would help to remove them. How do I do that from the terminal?
EDIT: I tried that, but it didn't work.

EDIT EDIT: I solved it! This did the trick:
```
sudo mv /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1.2.OLD
```

EDIT EDIT EDIT: I got the same Mesa problems as everyone else. I also think I found a solution here: [http://www.ubuntuforums.org/showthread.php?t=197471&highlight=libGL.so.1.2](http://www.ubuntuforums.org/showthread.php?t=197471&highlight=libGL.so.1.2).
It's pretty unclear. I'm trying it myself, I'll report back on how things go.

---

### Post by barney_1 on 2006-06-29
I have the same hang on Blank Screen before login as well.  This driver did not fix the problem.  It looks like I had acceleration working according to Xorg.0.log but if I can't log in it's worthless.

---

### Post by bassliu on 2006-06-29
tarkus@nnkh:~$ fglrxinfo 
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

---

### Post by Rojahon on 2006-06-29
[QUOTE=TD-Linux]I followed your instructions the first time, but I messed up and forgot to install the *.deb's :P

The second time, when I got to installing the *.debs, the first one (the xorg one) gives me an error copying libGL.so.1.2. It appears that it detected that it was a diversion, and tried to move it to a backup directory, but libGL.so.1.2 was there also. Should I remove libGL.so.1.2 from that directory, or what?

I think I have the official Ubuntu fglrx packages installed also. Maybe it would help to remove them. How do I do that from the terminal?
EDIT: I tried that, but it didn't work.

EDIT EDIT: I solved it! This did the trick:
```
sudo mv /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1.2.OLD
```

EDIT EDIT EDIT: I got the same Mesa problems as everyone else. I also think I found a solution here: [http://www.ubuntuforums.org/showthread.php?t=197471&highlight=libGL.so.1.2](http://www.ubuntuforums.org/showthread.php?t=197471&highlight=libGL.so.1.2).
It's pretty unclear. I'm trying it myself, I'll report back on how things go.[/QUOTE]

bump

I have been playing with different ideas from that thread but I haven't gotten anything to work.  Anyone else having any luck?

---

### Post by bvchurch on 2006-06-29
Well I posted earlier in the thread with this post
[http://ubuntuforums.org/showpost.php?p=1191937&postcount=15](http://ubuntuforums.org/showpost.php?p=1191937&postcount=15)

Today I tried a different monitor on this video card, an Acer AL1916ASD (digital, analog, silver color) and the same problem.

Basically I get an error when I run either of these
$ fglrxinfo
Error: couldn't find RGB GLX visual!

$ glxgears
Error: couldn't get an RGB, Double-buffered visual

The only conclusion I can come to is that for some reason Ubuntu, Kubuntu, and  Suse will not work with the downloaded newest driver and newly compiled 2.6.17. 1 kernel do not like my x800xl AIW.

So as for now I am heading back to mepis.

Now there is only one other possibility I can think of is that 64 bit drivers do not work properly for my card.  I may try a 32bit installation of ubuntu because I think this may be part of the problem....I doubt it, but eh who knows.

---

### Post by fitzman49 on 2006-06-30
Rojahon: I had to reconfigure xorg before I got mine working.  Do sudo dpkg-reconfigure xserver-xorg and make sure u have dri enabled to load when you are prompted.  Then just restart.  Let me know how it goes.

---

### Post by fitzman49 on 2006-06-30
There are now 64 bit drivers available from the ATI website.  I threw a link on the howto.  Also you can find the cards that are compatible with the 8.26.18 drivers here: [Driver List]("https://www2.ati.com/drivers/linux/linux_8.26.18.html")

---

### Post by Rojahon on 2006-06-30
[QUOTE=fitzman49]Rojahon: I had to reconfigure xorg before I got mine working.  Do sudo dpkg-reconfigure xserver-xorg and make sure u have dri enabled to load when you are prompted.  Then just restart.  Let me know how it goes.[/QUOTE]

That didn't seem to work..

Here's my xorg file if you can catch anything that needs to be changed.
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
	Option		"XkbLayout"	"dvorak"
	Option		"XkbOptions"	"altwin:meta_win"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
EndSection

Section "Monitor"
	Identifier	"Laptop LCD"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor		"Laptop LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600"
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

---

### Post by fitzman49 on 2006-06-30
Looks like you didnt run the last piece of the install.  Do this:

```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
```

Thats all I see right now.  Ill look at it closer tomorrow.  BTW if you would like, you can look at my xorg.conf to notice any changes.

You should have:

```
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
```

under a device heading like my xorg.conf

**My xorg.conf**

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
	Identifier   "AL1711"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Driver      "fglrx"
	VideoRam    64000
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Monitor    "AL1711"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

### Post by Craig Watson on 2006-06-30
@ DiamondX
I also have a radeon 9200 (plus recently a pci 9250, haven't really tested it yet) and I also had the same problems as you with the previous driver (haven't been able to try these, they wouldn't install) and after weeks of frustration I realised that all cards up to the radeon 9250 are supported by the free "radeon" driver, with hardware 3d :roll: . I get around 1400fps in glxgears, almost the same thing as with the proprietary drivers.

---

### Post by Rojahon on 2006-06-30
@fitzman49,

I ran those commands and added the lines you told me to.  Didn't seem to work.

I compared your xorg and mine they are pretty much identical.  That makes me think maybe it's not an xorg problem.

my new xorg just in case.
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
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
	Option	    "XkbLayout" "dvorak"
	Option	    "XkbOptions" "altwin:meta_win"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier   "Laptop LCD"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "fglrx"
	VideoRam    131072
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Laptop LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

### Post by Petarded on 2006-06-30
Hi,

I followed the instructions and the installation went without a hitch.
When I restart x server fails to load.
I read the log file and it has an error

```
(--) Log file: "/var/log/Xorg.0.log"' Time: Fri Jun 30 11:03:57 2006
(--) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected

Fatal server error:
no screens found
```

I'm running a Sony laptop PCG-K13 with a ATI Radeon 345M on Dapper

Any type of help would be great.

Update:
I just tried *fglrxinfo* and it gave me an error

```
Error: unable to open display :0
```

---

### Post by syxbit on 2006-06-30
first time i installed them just by running 
sudo sh ati.... etc..
and it worked just fine!, only since i'd run the repo's drivers earlier, i get getting an "update" for the old drivers.
i didn't know how to disable it. when i ran the update, it messed stuff up.
i did a reinstall of Dapper, and followed the instructions, and it works perfectly.
when ATI comes out with new drivers, how would i go about uninstalling these.
is it 
dpgk -r ... ?
appreciate the help

---

### Post by TD-Linux on 2006-06-30
Hmmm... maybe looking at how to install Mesa would help. I'll go look there and see what files make MESA run.
Okay, I looked, and MESA consists of one file: libGL.so. So, I guess the ATI version must have MESA in it to fall back on, or something.
Oh wait.... I didn't have the Ubuntu kernel source installed when I compiled the drivers and modules and stuff. Did I need that or something weird?

---

### Post by fitzman49 on 2006-06-30
@syxbit

What I did to uninstall the 8.24.18 drivers and upgrade to these was I went into synaptic and rolled back the drivers to the 8.25.8 drivers in the repositories.  After that i went into /usr/src and did:

```
sudo rm fglrx-kernel-*
```

This will remove the deb file that is made when you use the make and update command in the module assistant.  Then just follow the how to with the new drivers and they should work just the same.

---

### Post by fitzman49 on 2006-06-30
@Petarded

Since X is failing to load im guessing that all you get is a console.  If that is the case try:

```
sudo dpkg-reconfigure xserver-xorg
```

make sure that you choose the fglrx driver and not the ati driver.  If that doesnt work try to paste your xorg.conf on here and I will take a look at it.

---

### Post by TD-Linux on 2006-06-30
Yay! I got it working! Basically, you will need to check out the wiki:
[Wiki Link]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually")
My installation is an upgrade from Breezy. So, I did the steps there to uninstall the old drivers (see the section "Troubleshooting for Method 2 \ Upgrade from Breezy"). Then, I blacklisted fglrx. I'm not sure which one did it for me, possibly both.

So, blacklist fglrx first, by using your favorite text editor on /etc/default/linux-restricted-modules-common. It says how to do it more specifically in the Wiki, look there. If that dosen't work, then try the steps under the "Upgrade from Breezy" section, then start Method 2 from the beginning. It worked for me just perfect :D :D :D

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO Generic
OpenGL version string: 2.0.5879 (8.26.18)
```

```
$ glxgears -printfps
28701 frames in 5.0 seconds = 5740.053 FPS
```

---

### Post by Pawel on 2006-06-30
Hello!

In my case - it doesn't work. New version of ATI driver still cause that picture on monitor is to high when TV is connected :( 
My video card is Radeon 9200 SE. 

And one notice from me: the new drivers now hang the system when i try to switch between text mode and graphic mode so... - ehhh - i return to radeon open source drivers but how to enable TV-out with this drivers ?

Best Regards
Pawe&#322;

---

### Post by doog on 2006-06-30
Well, I just wasted another hour on this and still this ATI driver does NOT WORK with the Express 200M chip using onboard Sideport video memory. This was a fresh Ubuntu 6.0.6 install, update, and then build of the 8.26.18 driver to .deb.

As before, if I totally disable the faster Sideport memory and use 100% UMA/shared vidoe memory then the driver works fine. Albeit slow.

This is on a Compaq R4000 using the ATI Radeon Express 200M with 128MB onboard.  And as before, I had to add [ Option "no_dri" "yes" ] to the fglrx Driver section of xorg.conf for this to run in 2D-only mode using the 128MB of Sideport memory.

So this driver is STILL BROKEN with regard to the ATI RADEON EXPRESS 200M

---

### Post by dave1507 on 2006-06-30
Hi, I followed the instructions in the original post and flgrxinfo says:

OpenGL vendor string: ATI Technologies Inc
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.5879 (8.26.18)

which I think is how it should be. However all of the menus are invisible unless you move the mouse over them and all buttons are invisible unless you mouse over them. Also when you scroll in something eg Firefox everything becomes unreadable as some text stays where it is and some moves etc. Has this happened to anyone else? Please help because it is unusable at the moment.

Edit: Someone else has the same problem here [http://ubuntuforums.org/showthread.php?p=1199665#post1199665](http://ubuntuforums.org/showthread.php?p=1199665#post1199665)

anyone have any idea how to fix it?

---

### Post by syxbit on 2006-06-30
thanks fitzman
i ended up just formatting, and installed these drivers as instructed (as before, when i uninstalled the repo's, they kept annoying me about updates for it)
my Q was how would I uninstall THESE drivers once newer ones come out
thanks

---

### Post by Petarded on 2006-06-30
@fitzman49

The 'sudo dpkg-reconfigure' didn't work. I went through all the steps and it had the same error.

Here's my xorg.conf

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
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

Thanks for helping me out.

---

### Post by jhr79 on 2006-06-30
[QUOTE=doog]Well, I just wasted another hour on this and still this ATI driver does NOT WORK with the Express 200M chip using onboard Sideport video memory. This was a fresh Ubuntu 6.0.6 install, update, and then build of the 8.26.18 driver to .deb.

As before, if I totally disable the faster Sideport memory and use 100% UMA/shared vidoe memory then the driver works fine. Albeit slow.

This is on a Compaq R4000 using the ATI Radeon Express 200M with 128MB onboard.  And as before, I had to add [ Option "no_dri" "yes" ] to the fglrx Driver section of xorg.conf for this to run in 2D-only mode using the 128MB of Sideport memory.

So this driver is STILL BROKEN with regard to the ATI RADEON EXPRESS 200M[/QUOTE]

doog, in case you didn't know, you can use older driver that works. Check e.g.  the following [http://ubuntuforums.org/showthread.php?t=202250](http://ubuntuforums.org/showthread.php?t=202250)

---

### Post by bvchurch on 2006-06-30
I had posted two posts in this thread and i believe this is the final followup.

Basically I had a problem where fglrxinfo, glxgears, glxinfo would not run giving me an error "RGB visual not found" or something comparable.  
Ubuntu 6.06 64 bit edition, running ATI 8.25 and .26, neither of which Open GL would work on.  i also tried kernels 2.15 and 2.17 no luck on either

Ubuntu 6.06 32bit edition, running ATI 8.25 and .26, and 2.15 and 2.17 kernels all proved to be successful

glxgears -printfps will start out at around 9000 FPS and then it quickly goes to 13000 FPS.

Works great.

---

### Post by syxbit on 2006-06-30
my glxgears score nowhere near that good.
it's weird too, cause my score starts at 1300, but if i minimize the window it goes to 6000,
is this normal (i know it should make sense, as if you're not showing it onscreen it isn't rendering)

---

### Post by syxbit on 2006-06-30
my glxgears score nowhere near that good.
it's weird too, cause my score starts at 1300, but if i minimize the window it goes to 6000,
is this normal (i know it should make sense, as if you're not showing it onscreen it isn't rendering)
i have an ATI x1400, what card are you using that gets you 13k ?

---

### Post by alexlacasa86 on 2006-07-01
I follow the instructions and everything seems to be right. I will reboot now... I hope to be here in five minutes and not in a black screen...

---

### Post by alexlacasa86 on 2006-07-01
Well... I have returned... But it doesn't work...

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I'll never have 3D accel with my radeon xpress 200m :( :(

---

### Post by tommohawk on 2006-07-01
[QUOTE=alexlacasa86]Well... I have returned... But it doesn't work...

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I'll never have 3D accel with my radeon xpress 200m :( :([/QUOTE]

Yes you will - there are still issues with the ATI drivers for this card.  I don't trust any driver to work properly except the 8.24.8 one.  It is the only driver in recent months that I can get to work.  I am running an HP laptop with a Xpress200M card.  My screen runs at 1440x900, full XGL desktop and full 3D acceleration - So it can be done.  Look at this thread to find out how I did it and give it a try.

[http://www.ubuntuforums.org/showthread.php?t=197471&page=3](http://www.ubuntuforums.org/showthread.php?t=197471&page=3)

---

### Post by Moldy Jello on 2006-07-01
dude i followed your directions, first try, i was using the 8.25 drivers and just did what you said, now it works with the 8.26 drivers and i get about 40 fps faster in glgears, thanks a billion for the how to

---

### Post by crag277 on 2006-07-01
It's a shame it didn't work for you, but you post is not correct.  This process does work for some Xpress200M chips.  I just did a flawless install on my Compaq V2000Z which has Turion 64 and Xpress 200M.

---

### Post by kizz on 2006-07-01
Can someone help me with editing xorg.conf? I don't know where to put Identifier "aticonfig-Screen[0]", and the other thing... 
PM quick if YOU have the answer :)

---

### Post by newzero on 2006-07-01
[QUOTE=alexlacasa86]Well... I have returned... But it doesn't work...

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I'll never have 3D accel with my radeon xpress 200m :( :([/QUOTE]

I got the same error and I noticed something went wrong during the setup.

The error was at this part:
```
 Compile the kernel module:
Code:
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```

Just run this instead for a correct setup
```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod
```

I hope this helps and if yes then please correct the first post :)

kthxbai
-newzero

---

### Post by bitcowboy on 2006-07-01
I can't build the kernel module, anyone can help me?

```
dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
		cat /usr/src/modules/fglrx/debian/control.template > /usr/src/modules/fglrx/debian/control; \
	fi
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \
		mv /usr/src/modules/fglrx/debian/postinst /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.15-25-686.postinst; \
	fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-686'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
  LD [M]  /usr/src/modules/fglrx/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/modules/fglrx/.libfglrx_ip.a.GCC4.cmd for /usr/src/modules/fglrx/libfglrx_ip.a.GCC4
  CC      /usr/src/modules/fglrx/fglrx.mod.o
  LD [M]  /usr/src/modules/fglrx/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-686'
dh_testdir
dh_testroot
dh_clean -k
rm -f /usr/src/modules/fglrx/debian/control /usr/src/modules/fglrx/debian/dirs
sed -e 's/#KVERS#/2.6.15-25-686/g' \
	    -e 's/#VERSION#/8.26.18-1/g' debian/control.template > /usr/src/modules/fglrx/debian/control
sed -e 's/#KVERS#/2.6.15-25-686/g' debian/dirs.template > /usr/src/modules/fglrx/debian/dirs
dh_installdirs
dh_install fglrx.ko lib/modules/2.6.15-25-686/misc
dh_testdir
dh_testroot
dh_installdocs
dh_installmodules
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_gencontrol -- -v8.26.18-1+2.6.15-25.43 -VXSERVER=xorg
dh_md5sums
dh_builddeb --destdir=/usr/src
dpkg-deb&#65306;&#27491;&#22312;&#26032;&#24314;&#36719;&#20214;&#21253;“fglrx-kernel-2.6.15-25-686”&#65292;&#21253;&#25991;&#20214;&#20026;“/usr/src/fglrx-kernel-2.6.15-25-686_8.26.18-1+2.6.15-25.43_i386.deb”&#12290;
dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
Build time: 4 seconds

```

---

### Post by alexlacasa86 on 2006-07-02
[QUOTE=newzero]I got the same error and I noticed something went wrong during the setup.

The error was at this part:
```
 Compile the kernel module:
Code:
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```

Just run this instead for a correct setup
```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod
```

I hope this helps and if yes then please correct the first post :)

kthxbai
-newzero[/QUOTE]

Don't work for me, after doing this I reboot and... What a beautifull "black screen"!!

---

### Post by kstewart83 on 2006-07-02
Hello all,

I am interested in following these procedures to update my drivers. I'm fairly new to Ubuntu but I was impressed that my card worked right after install. The only problem is I don't get any 3D acceleration. 

When I first switched to Linux on this machine I used Gentoo and dealt with the black screen when starting X for about 3 days...very frustrating. That being said, I am interested to know exactly what files I need to backup before updating the drivers. I figure at least the xorg.conf file. If anyone could help me out, I would appreciate it.

---

### Post by moparfan90 on 2006-07-02
I have a ati X800GTO. would these drivers work with my card? the older drivers dont because of the GTO in the name
(agp)

---

### Post by fitzman49 on 2006-07-03
@kstewart83

Just follow the guide on the first page of this thread.  You do not need to back up any files to do this.  First time I did this procedure I had 3d acceleration with my xpress 200m.

---

### Post by fitzman49 on 2006-07-03
@moparfan90

There is a link on the first post of this thread that will tell what cards are compatible for the new 8.26.18 drivers

---

### Post by jpkotta on 2006-07-03
Modified the wiki to follow this, because the previous wiki page didn't work for me.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Moldy Jello on 2006-07-03
hi, does anyone here know how to enable the sideport+UMA stuff on the compaq v2000 series, i have that one and i am not sure on how to do that, i looked all in my BIOS and i did not see it

---

### Post by Moldy Jello on 2006-07-03
oh and i had my card working following this here  [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)  and using the first method, i just saw that when i do it i get the generic driver after it and a little bit slower fps than other people who did not have generic, i would post the output but it is in the middle of a reformat

---

### Post by brickhead20 on 2006-07-03
```
sudo sh ati-driver-installer-8.26.18-x86.run
```

Just use this! It works fine for me and saves all the effort. It opens up a graphical interface, and when you restart all your problems have gone.

---

### Post by doog on 2006-07-03
[QUOTE=crag277]It's a shame it didn't work for you, but you post is not correct.  This process does work for some Xpress200M chips.  I just did a flawless install on my Compaq V2000Z which has Turion 64 and Xpress 200M.[/QUOTE]

crag277, I just looked up your V2000Z and it does not come with onboard video memory, only shared( UMA ) video memory...and therefore, you'll get 3D working using this method.  What I was talking about was for all those who have laptops with high speed ONBOARD video memory( called Sideport memory ). In this case, this proceedure still fails and many of use actually paid extra from HP/Compaq to get this kind of video memory. :(

---

### Post by kstewart83 on 2006-07-04
I went through the guide and when I rebooted I couldn't control the mouse or the keyboard and some of my tray icons were replaced with question marks. GDM seemed to have loaded normally (at least no black screen), but I noticed some wierd things when I tried changing the session to Terminal Failsafe. The buttons to change the session wouldn't actually appear until I moved my mouse over that area. When I loaded the failsafe terminal, 'clear' wouldn't clear anything and 'exit' didn't do anything either.

After some hard resets I used the recovery mode to restore my old xorg.conf file and everything loaded up fine. I have a HP Pavilion zv6000 with the ATI Xpress 200m and 128 MB of sideport memory enabled. Here is what fglrxinfo gives me when I'm running under the working xorg.conf:

~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d](www.mesa3d). org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Any ideas on what I should be looking for in the xorg.conf file? It has been a while since I've messed with one.

Thanks

---

### Post by jhr79 on 2006-07-04
[QUOTE=kstewart83]I went through the guide and when I rebooted I couldn't control the mouse or the keyboard and some of my tray icons were replaced with question marks. GDM seemed to have loaded normally (at least no black screen), but I noticed some wierd things when I tried changing the session to Terminal Failsafe. The buttons to change the session wouldn't actually appear until I moved my mouse over that area. When I loaded the failsafe terminal, 'clear' wouldn't clear anything and 'exit' didn't do anything either.

After some hard resets I used the recovery mode to restore my old xorg.conf file and everything loaded up fine. I have a HP Pavilion zv6000 with the ATI Xpress 200m and 128 MB of sideport memory enabled. Here is what fglrxinfo gives me when I'm running under the working xorg.conf:

~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d](www.mesa3d). org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Any ideas on what I should be looking for in the xorg.conf file? It has been a while since I've messed with one.

Thanks[/QUOTE]


I'm having exactly the same machine and only way to get it to work is to use older driver version and Sideport+UMA mode (check [this]("http://ubuntuforums.org/showthread.php?t=202250")).

---

### Post by bvchurch on 2006-07-04
[QUOTE=syxbit]my glxgears score nowhere near that good.
it's weird too, cause my score starts at 1300, but if i minimize the window it goes to 6000,
is this normal (i know it should make sense, as if you're not showing it onscreen it isn't rendering)
i have an ATI x1400, what card are you using that gets you 13k ?[/QUOTE]

I have an Athlon 64 3200, 1GB Mosel Vitelic 2700, ATI X800XL AIW, on a Gigabyte K8NS Ultra motherboard.  

Now I am just fighting with sound card issues, specificlly mic issues, but thats another topic.

---

### Post by Steven_B on 2006-07-04
> my glxgears score nowhere near that good.
it's weird too, cause my score starts at 1300, but if i minimize the window it goes to 6000,
is this normal (i know it should make sense, as if you're not showing it onscreen it isn't rendering)
That's fairly normal.  1300 fps is good enough to play planetpenguin racer. :D 

Sorry if this has been asked before, but when will this be available in the repositories?  Will we have to wait for Edgy?

---

### Post by kstewart83 on 2006-07-04
Its working now. I downloaded the 8.24.8 drivers and followed the same procedures I followed for the 8.26 install. I didn't have to recompile the kernel or replace any specific libraries. I have Sidport+UMA (128 + 128) enabled. Thanks jhr79 and tommohawk for pointing me in the right direction.

---

### Post by naruto1974 on 2006-07-04
[QUOTE=fitzman49]Finally ATI released the much anticipated update to the fglrx driver which now has support for xorg 7.0 and works with all xseries cards.  Mine (xpress 200m) did not work with the fglrx 8.25.18 drivers but now have full support and 3D acceleration.  These drivers also address the black screen hanging issue when xorg is shutdown or restarted.  Heres a quick tutorial on how I got it working.  Much thanks to IVHassel for the tutoiral before that I used to get the old drivers working.:) 

Cards that are known to work with these new drivers can be found here: [https://www2.ati.com/drivers/linux/linux_8.26.18.html]("https://www2.ati.com/drivers/linux/linux_8.26.18.html")


Installing the new driver

Download the ATI driver installer from the ATI Website: 32bit Installer:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run]("https://www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run")

**Edit:**64 bit users:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run]("https://www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run")

This guide refers to the 32bit version of the driver. If you are using a x86_64 System you need the 64bit Installer. The installation procedure should be the same as for 32bit, except some filenames will differ slightly.

Change to the download directory...


"Change to the download directory."???...How do I do that?  do you mean inside the terminal?...if so how do I do that?...I dont see any instructions on how to navigate in the terminal anywhere. This is the most complex hardware install I've ever had to do, I'm used to windows simplicity in this area. I'm starting to wonder should I just give up on my Radeon 9800pro and go buy a nvida card? would it make the installing process any easier?

---

### Post by Dimas on 2006-07-04
I have the same problem that have reported others... After installing the new drivers with this post method and reboot, Mesa is rendering and fglrx has gone...

I can see this in my /var/log/Xorg.0.log:



```

X Window System Version 7.0.0
X Protocol Version 11, Revision 0, Release 7.0
Current Operating System: Linux 2.6.15-25-386 #1

(...)

(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
compiled for 6.8.99.8, module version = 8.26.18
Module class: X.Org Video Driver
ABI class: X.Org Video Driver, version 0.7

(...)

(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	**compiled for 6.8.99.8**, module version = 8.26.18
	ABI class: X.Org Server Extension, version 0.2
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)

(...)

[B](II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0[/B]

(...)

(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7196000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     **Version: 8.25.18**
(II) fglrx(0):     Date: May 18 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
**(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work**
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7196000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

I don't know how to solve it :(

---

### Post by Steven_B on 2006-07-04
> "Change to the download directory."???...How do I do that? do you mean inside the terminal?...if so how do I do that?...I dont see any instructions on how to navigate in the terminal anywhere
```
cd the_directory_you_want_to_change_to
```
Put quotes around it if the directory name contains spaces.  This is case sensitive.

---

### Post by fitzman49 on 2006-07-04
> (II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.25.18
(II) fglrx(0):     Date: May 18 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work

@Dimas

Looks like your main problem is that you dont have the right kernel module installed for the 8.26.18 drivers.  If you have the 8.25.18 kernel modules installed make sure you remove them first before you install the .debs that you made. After those are removed try the guide again.

---

### Post by fitzman49 on 2006-07-04
This is the kind of fps I get from my xpress 200m if anyone is curious what they should expect from their card.

```
[fitzy@greenmachine49]~ glxgears -printfps
3894 frames in 5.0 seconds = 778.593 FPS
3943 frames in 5.0 seconds = 788.347 FPS
3942 frames in 5.0 seconds = 788.389 FPS
3936 frames in 5.0 seconds = 787.021 FPS
3931 frames in 5.0 seconds = 786.037 FPS

```

---

### Post by crashtestyyz on 2006-07-04
Short of re-installing my nearly-fresh first-ever install of Ubuntu on my amd64,  I'm out of ideas.
I installed the ATI drivers manually (as an alien'd package)
THEN, I sh'd the installer, which went okay after I installed a lot of required packages.
THEN I discovered this forum.   I followed fitzman's instructions, and seemed to need more packages.  At any rate, everything went in, installed, compiled, with no errors.

Regardless, since the first time the server actually ran, I've had the following error:

```
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) fglrx(0): PreInitDAL failed
(EE) fglrx(0): R200PreInit failed
```

In the Xorg.0.log file, I see the following:
```

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON X1600 Series (RV530 71C2) found
```

At this point I also have a modified kernel (via fitzman's instructions) but don't know how to load it from GRUB - a slightly off-topic but somewhat-related problem :)

I've already wasted a few long evenings on this.. can anybody suggest anything?
--C

---

### Post by Dimas on 2006-07-05
[QUOTE=fitzman49]@Dimas

Looks like your main problem is that you dont have the right kernel module installed for the 8.26.18 drivers.  If you have the 8.25.18 kernel modules installed make sure you remove them first before you install the .debs that you made. After those are removed try the guide again.[/QUOTE]

Yes, looks like my fglrx kernel module is the 8.25.18 version, and the installation of 8.26.18 don't update it. I've a 2.6.15-25-386 kernel, I tried to reinstall headers, restricted-modules, xorg-fglrx-driver... and kernel module continue with 8.25.18.

How can I update the fglrx kernel module???

Thx

---

### Post by james016 on 2006-07-05
[QUOTE=fitzman49]Finally ATI released the much anticipated update to the fglrx driver which now has support for xorg 7.0 and works with all xseries cards.  Mine (xpress 200m) did not work with the fglrx 8.25.18 drivers but now have full support and 3D acceleration.  These drivers also address the black screen hanging issue when xorg is shutdown or restarted.  Heres a quick tutorial on how I got it working.  Much thanks to IVHassel for the tutoiral before that I used to get the old drivers working.:) 

Cards that are known to work with these new drivers can be found here: [https://www2.ati.com/drivers/linux/linux_8.26.18.html]("https://www2.ati.com/drivers/linux/linux_8.26.18.html")


Installing the new driver

Download the ATI driver installer from the ATI Website: 32bit Installer:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run]("https://www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run")

**Edit:**64 bit users:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run]("https://www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run")

This guide refers to the 32bit version of the driver. If you are using a x86_64 System you need the 64bit Installer. The installation procedure should be the same as for 32bit, except some filenames will differ slightly.

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

Install necessary tools:
```
sudo apt-get update 
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```



Create .deb packages:

```
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
```


Install .deb packages:

```
sudo dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb 
sudo dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb 
sudo dpkg -i fglrx-control_8.26.18-1_i386.deb
```


Remove any old fglrx deb's from /usr/src/:

```
sudo rm /usr/src/fglrx-kernel*.deb
```


Compile the kernel module:

Code:

```
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```


Note: You have to recompile the kernel module after each kernel update!

Update the xorg.conf file:

```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
```


Reboot.

Confirm that it worked


```
[fitzy@greenmachine49]~ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series Generic
OpenGL version string: 2.0.5879 (8.26.18)
```




If you have any questions feel free to post here or private message me and I will try to help as best as possible.\\:D/[/QUOTE]

I have a question regarding the kernel updating. Once the new kernel has been downloaded and installed you run the commands to compile it before you reboot?

Kernel updated come through the auto update facility?

---

### Post by caish5 on 2006-07-05
Hi peoples,

I have a Sony Vaio PCG-K17 laptop with ati graphics and i've been trying to get this driver to work. There were no errors during the process at all untill i restarted X. Then i got the fatal error, no screens found.

The output of my Xorg.0.log is as follows.....

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux vaio 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul  6 03:42:33 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,cbb2 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,7010 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10b9,5457 card 104d,8175 rev 00 class 07,03,00 hdr 00
(II) PCI: 00:04:0: chip 10b9,5451 card 104d,8175 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10b9,7101 card 104d,8175 rev 00 class 06,80,00 hdr 00
(II) PCI: 00:07:0: chip 10b9,1533 card 104d,8175 rev 00 class 06,01,00 hdr 00
(II) PCI: 00:09:0: chip 168c,0013 card 1468,0406 rev 01 class 02,00,00 hdr 00
(II) PCI: 00:0a:0: chip 104c,ac8e card 1400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 00:0a:2: chip 104c,802e card 104d,8175 rev 00 class 0c,00,10 hdr 80
(II) PCI: 00:0a:3: chip 104c,ac8f card 104d,8175 rev 00 class 01,80,00 hdr 80
(II) PCI: 00:0c:0: chip 1033,0035 card 104d,8175 rev 43 class 0c,03,10 hdr 80
(II) PCI: 00:0c:1: chip 1033,0035 card 104d,8175 rev 43 class 0c,03,10 hdr 00
(II) PCI: 00:0c:2: chip 1033,00e0 card 104d,8175 rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:0f:0: chip 10b9,5229 card 104d,8175 rev c4 class 01,01,fa hdr 00
(II) PCI: 00:12:0: chip 10ec,8139 card 104d,8175 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:05:0: chip 1002,4337 card 104d,8175 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0300000 - 0xe03fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,5), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[1] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x32000000 - 0x33ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x31ffffff (0x2000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc Radeon IGP 330M/340M/350M rev 0, Mem @ 0xf0000000/27, 0xe0300000/16, I/O @ 0xa000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xefffffff to 0xe7ffffff
(II) PCI Memory resource overlap reduced 0xe0600000 from 0xe0600fff to 0xe05fffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe000bc00 - 0xe000bdff (0x200) MX[B]
	[1] -1	0	0xe000b800 - 0xe000b8ff (0x100) MX[B]
	[2] -1	0	0xe000a000 - 0xe000afff (0x1000) MX[B]
	[3] -1	0	0xe0009000 - 0xe0009fff (0x1000) MX[B]
	[4] -1	0	0xe0007000 - 0xe0007fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xe0003fff (0x4000) MX[B]
	[6] -1	0	0xe000b000 - 0xe000b7ff (0x800) MX[B]
	[7] -1	0	0x34000000 - 0x3400ffff (0x10000) MX[B]
	[8] -1	0	0xe0005000 - 0xe0005fff (0x1000) MX[B]
	[9] -1	0	0x34010000 - 0x34010fff (0x1000) MX[B]
	[10] -1	0	0xe0600000 - 0xe05fffff (0x0) MX[B]O
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xe0300000 - 0xe030ffff (0x10000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[15] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[16] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[17] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe000bc00 - 0xe000bdff (0x200) MX[B]
	[1] -1	0	0xe000b800 - 0xe000b8ff (0x100) MX[B]
	[2] -1	0	0xe000a000 - 0xe000afff (0x1000) MX[B]
	[3] -1	0	0xe0009000 - 0xe0009fff (0x1000) MX[B]
	[4] -1	0	0xe0007000 - 0xe0007fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xe0003fff (0x4000) MX[B]
	[6] -1	0	0xe000b000 - 0xe000b7ff (0x800) MX[B]
	[7] -1	0	0x34000000 - 0x3400ffff (0x10000) MX[B]
	[8] -1	0	0xe0005000 - 0xe0005fff (0x1000) MX[B]
	[9] -1	0	0x34010000 - 0x34010fff (0x1000) MX[B]
	[10] -1	0	0xe0600000 - 0xe05fffff (0x0) MX[B]O
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xe0300000 - 0xe030ffff (0x10000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[15] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[16] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[17] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x33ffffff (0x33f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x33ffffff (0x33f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe000bc00 - 0xe000bdff (0x200) MX[B]
	[5] -1	0	0xe000b800 - 0xe000b8ff (0x100) MX[B]
	[6] -1	0	0xe000a000 - 0xe000afff (0x1000) MX[B]
	[7] -1	0	0xe0009000 - 0xe0009fff (0x1000) MX[B]
	[8] -1	0	0xe0007000 - 0xe0007fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xe0003fff (0x4000) MX[B]
	[10] -1	0	0xe000b000 - 0xe000b7ff (0x800) MX[B]
	[11] -1	0	0x34000000 - 0x3400ffff (0x10000) MX[B]
	[12] -1	0	0xe0005000 - 0xe0005fff (0x1000) MX[B]
	[13] -1	0	0x34010000 - 0x34010fff (0x1000) MX[B]
	[14] -1	0	0xe0600000 - 0xe05fffff (0x0) MX[B]O
	[15] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[16] -1	0	0xe0300000 - 0xe030ffff (0x10000) MX[B](B)
	[17] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[21] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[22] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[23] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
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
	compiled for 6.8.99.8, module version = 8.26.18
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
	compiled for 7.0.0, module version = 1.0.3
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
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9250/9200 Series (RV280 5961),
	RADEON 9250/9200 Series (RV280 5962),
	RADEON 9250/9200 Series (RV280 5964), FireMV 2200 PCI (RV280 5965),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300/X550 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 SE (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600/X550 Series (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 GTO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), FireGL V7200 (R480 5D50),
	RADEON X850 XT (R480 5D52), RADEON X850 (R481 4B48),
	RADEON X850 XT (R481 4B49), RADEON X850 SE (R481 4B4A),
	RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), RADEON X700 XT (RV410 5E4A),
	RADEON X700 PRO (RV410 5E4B), RADEON X700 SE (RV410 5E4C),
	RADEON X700 (RV410 5E4D), RADEON X700/X550 Series (RV410 5E4F),
	MOBILITY RADEON X700 (M26 5652), MOBILITY RADEON X700 (M26 5653),
	MOBILITY RADEON X700 XL (M26-XC 564F),
	RADEON 9000/9100 IGP Series (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000 IGP (RL300MB 7835),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 XT (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 Series (R520 7108),
	RADEON X1800 Series (R520 7109), RADEON X1800 Series (R520 710A),
	RADEON X1800 Series (R520 710B), RADEON X1800 Series (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	RADEON X1300 PRO (RV505 7143), RADEON X1300 (RV505 7147),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1300 Series (RV505 715F), RADEON X1600 Series (RV515 7140),
	RADEON X1300 Series (RV515 7142), MOBILITY FireGL (M54 GL 7144),
	MOBILITY RADEON X1400 (M54 7145), RADEON X1300 Series (RV515 7146),
	MOBILITY RADEON X1300 (M52 7149), MOBILITY RADEON X1300 (M52 714A),
	RADEON X1300 Series (RV515 714D), RADEON X1300 Series (RV515 714E),
	FireGL V3300 (RV515 7152), RADEON X1300 Series (RV515 715E),
	RADEON X1300 (RV516 7180), RADEON X1300 (RV516 7183),
	MOBILITY RADEON X1450 (M64P 7186), RADEON X1300 (RV516 7187),
	MOBILITY RADEON X1350 (M62P 718B),
	MOBILITY RADEON X1350 (M62CSP64 718C),
	MOBILITY RADEON X1450 (M62CSP128 718D),
	MOBILITY RADEON X1350 (M62S 7196), RADEON X1900 (R580 7240),
	RADEON X1900 (R580 7243), RADEON X1900 (R580 7244),
	RADEON X1900 (R580 7245), RADEON X1900 (R580 7246),
	RADEON X1900 (R580 7247), RADEON X1900 (R580 7248),
	RADEON X1900 (R580 7249), RADEON X1900 (R580 724A),
	RADEON X1900 (R580 724B), RADEON X1900 (R580 724C),
	RADEON X1900 (R580 724D), RADEON X1900 (R580 724E),
	RADEON X1900 (R580 724F), RADEON X1600 Series (RV530 71C0),
	RADEON X1600 Series (RV530 71C2), MOBILITY FireGL V5200 (M56 71C4),
	MOBILITY RADEON X1600 (M56 71C5),
	RADEON X1600 Series (RV530 LE 71C6),
	RADEON X1600 Series (RV530 VE 71CE), FireGL V3400 (RV530 71D2),
	FireGL V5200 (RV530 71DA), RADEON X1600 Series (RV530 SE 71DE)
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.26.18
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.26g1                           
(II) ATI Proprietary Linux Driver Build Date: Jun 22 2006 12:50:04
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.26.1-driver-lnx-275228
(--) Assigning device section with no busID to primary device
(EE) No devices detected.

Fatal server error:
no screens found

```
Any help would be much appreciated..

Andy

---

### Post by d3x7r0 on 2006-07-05
Damn the kernel module won't compile in 2.6.17.3... :( And I was hopping that finnaly I would be able to use XGL but guess not yet... (agpgart only started supporting my chipset in v2.6.17.x)

Btw the error is complaining about a missing makefile.lib.c file :?

---

### Post by JonAre on 2006-07-05
After installing this driver I'm no longer able to adjust the LCD brightness on my HP nx6125 laptop. The fn+f9/f10 combo does nothing at all, and I can't find any other way of doing it either. The ATI Control Panel hasn't got this option. Any ideas?

---

### Post by james016 on 2006-07-05
I followed the instructions in the Wiki but my fglrxinfo comes out as:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Can't see where I went wrong

Also get this:

james@JK01:~$ dmesg | grep fglrx
[17179605.220000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologie s, Starnberg, GERMANY' taints kernel.
[17179605.220000] [fglrx] Maximum main memory to use for locked dma buffers: 929  MBytes.
[17179605.220000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179608.436000] [fglrx:firegl_unlock] *ERROR* Process 4424 using kernel contex t 0

---

### Post by hanspb on 2006-07-05
Hey, just to let you know: I have now followed 2 ways of installing this driver. first I tried the way described on ATI's website. That did not work. The ATI control panel was installed and worked, but no openGL. then I tried the method described in the first post of this thread, and it worked right away! The only problem is the fact that I have to recompile for every kernel update...
Well I'm happy, so good night!

Edit: --And I have the notorious Radeon Xpress 200M!

---

### Post by Dimas on 2006-07-05
Did you know if are correct these sections of my xorg.conf correct for 8.26 property drivers and ati 9700 ? I tried to enable/disable *Load "dri"* but the *[drm] failed to load kernel module "fglrx"* is there...

```
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

Section "DRI"
	Mode         0666
EndSection
```

Looks like the problem is DRI:

```
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

---

### Post by d-E-a-D on 2006-07-05
Ok, after more than 10 formats and thousand tries to make it work, i get 8.26 drivers working on my hp pavilion dv5172 with ati radeon Xpress 200m.
***_I'm using UMA+SIDEPORT 128Mb._***
It gives me the right fglrxinfo:

OpenGL vendor string: ATI technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5879 (***_8.26.18_***)

Now my issue is that glxgears and fglx_gears hangs when i try to run it _***but things like screensaver and games do it great on OpenGL and fps.***_ but it is unstable. sometimes crash, others not.

The worst issue is that it seems that it doesn't refresh the image, everything just is it seems that the windows are over ones of the others, I see the images overlapped, icones disappears when I open something over them and closes.
To read console i have to underline the mouse over the letters. but if i maximize the console i can read it all great.

Now the steps.
Fresh Install of Ubuntu 6.06
update
distro-upgrade
restart
follow this thread but ***_WITH 8.26.18 DRIVER DOWNLOADED FROM ATI_***:
[http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m]("http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m")
restart

For now i can't go further... does anyone goes further than this with 8.26.18 drivers?

NOTE: 8.24.18 drivers worked for me with the thread i said. but i can't get XGL and COMPIZ working. And with fglx_glxgears i just see one piece rolling, the others don't appear like in glxgears.

If someone have this 200M card working well and with XGL and COMPIZ please give us a HOW-TO step by step !!!!

SORRY MY BAD ENGLISH.

Cumps

---

### Post by Steven_B on 2006-07-06
> *Posted by Caish5*
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.26.1-driver-lnx-275228
(--) Assigning device section with no busID to primary device
(EE) No devices detected.

Fatal server error:
no screens found
@caish5
It sounds like you don't have any devices and/or screens in your xorg.conf, or the driver can't find them.  Could you post the Monitor, Device and Screen sections of your Xorg.conf?  For reference, mine looks like this (but I don't have GL acceleration working)
```

Section "Monitor"
	Identifier   "e15t4"
	HorizSync    50.0 - 61.0
	VertRefresh  60.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Driver		"fglrx"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
	BusID		"PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Monitor    "e15t4"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1024x768"
	EndSubSection
EndSection
```

---

### Post by JonAre on 2006-07-06
[QUOTE=JonAre]After installing this driver I'm no longer able to adjust the LCD brightness on my HP nx6125 laptop. The fn+f9/f10 combo does nothing at all, and I can't find any other way of doing it either. The ATI Control Panel hasn't got this option. Any ideas?[/QUOTE]

It turned out that I was missing more laptop spesific buttons, like the "sensor" for the lid and power button. I compared by backed up xorg.conf and I noticed that the following section was missing in the new version:

```

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

```

With this back in action the lid and power button works like before, but still no luck with the LCD brightness.

---

### Post by caish5 on 2006-07-06
thanks for the reply steven B...

```

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768"
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

### Post by utherwayn on 2006-07-06
Ok followed the directions in this howto and got this from my xorg log, i had to truncate it a little to get it to fit.  I think its a DRI initialization issue but I didn't see a clear answer in here as to how to get that fixed?  More information following this post.

Xorg.0.log
```

(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.25.18
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
	compiled for 7.0.0, module version = 1.0.3
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
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9000 (RV280 5962),
	RADEON 9200 SE (RV280 5964), FireMV 2200 PCI (RV280 5965),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600 (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), RADEON X850 XT (R480 5D52),
	RADEON X850 (R481 4B48), RADEON X850 XT (R481 4B49),
	RADEON X850 SE (R481 4B4A), RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), MOBILITY RADEON X700 XL,
	RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 XT (R520 7108),
	RADEON X1800 PRO (R520 7109), RADEON X1800 SE (R520 710A),
	RADEON X1800 (R520 710B), RADEON X1800 (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	RADEON X1300 PRO (RV505 7143), RADEON X1300 (RV505 7147),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1300 (RV505 715F), RADEON X1300 XT (RV515 7140),
	RADEON X1300 PRO (RV515 7142), MOBILITY FireGL (M54 GL 7144),
	MOBILITY RADEON X1400 (M54 7145), RADEON X1300 LE (RV515 7146),
	MOBILITY RADEON X1300 (M52 7149), MOBILITY RADEON X1300 (M52 714A),
	RADEON X1300 SE (RV515 714E), FireGL V3300 (RV515 7152),
	RADEON X1300 VE (RV515 715E), RADEON X1300 (RV516 7180),
	RADEON X1300 (RV516 7183), RADEON X1300 (RV516 7187),
	RADEON X1900 (R580 7240), RADEON X1900 (R580 7243),
	RADEON X1900 (R580 7244), RADEON X1900 (R580 7245),
	RADEON X1900 (R580 7246), RADEON X1900 (R580 7247),
	RADEON X1900 (R580 7248), RADEON X1900 (R580 7249),
	RADEON X1900 (R580 724A), RADEON X1900 (R580 724B),
	RADEON X1900 (R580 724C), RADEON X1900 (R580 724D),
	RADEON X1900 (R580 724E), RADEON X1900 (R580 724F),
	RADEON X1600 XT (RV530 71C0), RADEON X1600 PRO (RV530 71C2),
	MOBILITY FireGL V5200 (M56 71C4), MOBILITY RADEON X1600 (M56 71C5),
	RADEON (RV530 LE 71C6), RADEON (RV530 VE 71CE),
	FireGL V3400 (RV530 71D2), FireGL V5200 (RV530 71DA),
	RADEON (RV530 SE 71DE)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.25.18
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.25g1                           
(II) ATI Proprietary Linux Driver Build Date: May 18 2006 09:54:44
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.25.1-driver-lnx-268237
(--) Assigning device section with no busID to primary device
(--) Chipset MOBILITY RADEON X700 (M26 5653) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x54000000 - 0x5401ffff (0x20000) MX[B]
	[5] -1	0	0xc8005000 - 0xc8005fff (0x1000) MX[B]
	[6] -1	0	0xc8000000 - 0xc8003fff (0x4000) MX[B]
	[7] -1	0	0xc8004000 - 0xc80047ff (0x800) MX[B]
	[8] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[9] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[10] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[11] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[17] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[18] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[19] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[20] -1	0	0x00001874 - 0x00001877 (0x4) IX[B]
	[21] -1	0	0x00001890 - 0x00001897 (0x8) IX[B]
	[22] -1	0	0x00001898 - 0x0000189b (0x4) IX[B]
	[23] -1	0	0x000018a0 - 0x000018a7 (0x8) IX[B]
	[24] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[28] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81d9680
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x54000000 - 0x5401ffff (0x20000) MX[B]
	[5] -1	0	0xc8005000 - 0xc8005fff (0x1000) MX[B]
	[6] -1	0	0xc8000000 - 0xc8003fff (0x4000) MX[B]
	[7] -1	0	0xc8004000 - 0xc80047ff (0x800) MX[B]
	[8] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[9] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[10] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[11] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[20] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[21] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[22] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[23] -1	0	0x00001874 - 0x00001877 (0x4) IX[B]
	[24] -1	0	0x00001890 - 0x00001897 (0x8) IX[B]
	[25] -1	0	0x00001898 - 0x0000189b (0x4) IX[B]
	[26] -1	0	0x000018a0 - 0x000018a7 (0x8) IX[B]
	[27] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[28] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[29] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[31] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[32] 0	0	0xc01203b0 - 0xc01203bb (0xc) IS[B]
	[33] 0	0	0xc01203c0 - 0xc01203df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "MOBILITY RADEON X700 (M26 5653)" (Chipset = 0x5653)
(--) fglrx(0): (PciSubVendor = 0x1558, PciSubDevice = 0x04a0)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xc0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.10
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M26-P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
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
	compiled for 6.8.99.8, module version = 8.25.18
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR1
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0): Derived EDID from BIOS and internal tables for Display1:
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: MS_  Model: 0  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:Serration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 60  vid: 16497
(II) fglrx(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  0 x 0 mm
(II) fglrx(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1050  v_sync_end 1050 v_blanking: 1066 v_border: 0
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 11 modes found for primary display.
(--) fglrx(0): Virtual size is 1400x1050 (pitch 1408)
(**) fglrx(0): *Mode "1400x1050": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"  108.00  1400 1448 1560 1688  1050 1051 1054 1066
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1051 1054 1066
(**) fglrx(0): *Mode "1024x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  108.00  1024 1072 1184 1688  768 1051 1054 1066
(**) fglrx(0): *Mode "800x600": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  108.00  800 848 960 1688  600 1051 1054 1066
(**) fglrx(0): *Mode "640x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  108.00  640 688 800 1688  480 1051 1054 1066
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1200 1312 1688  864 1051 1054 1066
(**) fglrx(0):  Default mode "640x400": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  108.00  640 688 800 1688  400 1051 1054 1066
(**) fglrx(0):  Default mode "512x384": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  108.00  512 560 672 1688  384 1051 1054 1066
(**) fglrx(0):  Default mode "400x300": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  108.00  400 448 560 1688  300 1051 1054 1066
(**) fglrx(0):  Default mode "320x240": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  108.00  320 368 480 1688  240 1051 1054 1066
(**) fglrx(0):  Default mode "320x200": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  108.00  320 368 480 1688  200 1051 1054 1066
(--) fglrx(0): Display dimensions: (400, 300) mm
(--) fglrx(0): DPI set to (88, 88)
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
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): cpuSpeedMHz: 0x000007cb
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0100000 - 0xc010ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0x54000000 - 0x5401ffff (0x20000) MX[B]
	[7] -1	0	0xc8005000 - 0xc8005fff (0x1000) MX[B]
	[8] -1	0	0xc8000000 - 0xc8003fff (0x4000) MX[B]
	[9] -1	0	0xc8004000 - 0xc80047ff (0x800) MX[B]
	[10] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[11] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[12] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[13] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[14] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] 0	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[23] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[24] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[25] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[26] -1	0	0x00001874 - 0x00001877 (0x4) IX[B]
	[27] -1	0	0x00001890 - 0x00001897 (0x8) IX[B]
	[28] -1	0	0x00001898 - 0x0000189b (0x4) IX[B]
	[29] -1	0	0x000018a0 - 0x000018a7 (0x8) IX[B]
	[30] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[31] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[32] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[33] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[34] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[35] 0	0	0xc01203b0 - 0xc01203bb (0xc) IS[B]
	[36] 0	0	0xc01203c0 - 0xc01203df (0x20) IS[B]
(II) fglrx(0): UMM Bus area:     0xd07ad000 (size=0x07843000)
(II) fglrx(0): UMM area:     0xd07ad000 (size=0x07843000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x07ff0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1408,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1408,1050) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "UseFBDev" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1408 x 7137
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
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
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "en"
(**) Generic Keyboard: XkbLayout: "en"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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
Synaptics Touchpad no synaptics event device found (checked 13 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
AUDIT: Thu Jul  6 11:11:06 2006: 4395 X: client 4 rejected from local host
(WW) fglrx(0): ***********************************
(WW) fglrx(0): * DRI initialization disabled!    *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available    *
(WW) fglrx(0): ***********************************
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x07ff0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1408,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1408,1050) (front color buffer - assumption)
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1408 x 7137
(==) RandR enabled
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---

### Post by utherwayn on 2006-07-06
fglrxinfo
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

```

xorg.conf
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
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "en"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier   "Laptop LCD"
	HorizSync    28.0 - 50.0
	VertRefresh  43.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Mobility Radeon X700"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Mobility Radeon X700"
	Monitor    "Laptop LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

### Post by Dimas on 2006-07-06
I'm getting this curious error in my Xorg.0.log with drm module... any ideas?
ati 9700 / fglrx disabled in modules-restricted-common

```
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.26.18
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
```
But a few lines down...
```
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
```

---

### Post by fitzman49 on 2006-07-06
[QUOTE=utherwayn]fglrxinfo
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

```

xorg.conf
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
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "en"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier   "Laptop LCD"
	HorizSync    28.0 - 50.0
	VertRefresh  43.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Mobility Radeon X700"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Mobility Radeon X700"
	Monitor    "Laptop LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050" "1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```[/QUOTE]

@utherwayn

Seems that you are not loading the correct modules for xorg to use the fglrx drivers.  You should have something like:```
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
```

I would try doing a ```
sudo dpkg-reconfigure xserver-xorg
```

Make sure that you choose the fglrx driver and not the ati driver.  Also make sure you have the modules above checked when you are prompted for them.  When that is done restart X.

---

### Post by Steven_B on 2006-07-06
@caish5
In your second "Device" section add the line: "	BusID       "PCI:1:5:0""
```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	**BusID       "PCI:1:5:0"**
EndSection
```

@utherwayn
You are missing a bunch of modules.  You should be able to copy fitzman49's  module section into your xorg.conf, in place of the empty module section.

---

### Post by t.lauckner on 2006-07-06
Hello you all,

I have similar problems, but only *similar*. Today I got my fglrx running, but what happens if you try this (do you have an Idea what 2 do? DRI is 0666):

```

thomas@silverstar:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

thomas@silverstar:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  33
  Current serial number in output stream:  33
thomas@silverstar:~$ sudo fglrxinfo]
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.5814 (8.25.18)

thomas@silverstar:~$ sudo fgl_glxgears
Using GLX_SGIX_pbuffer
1243 frames in 5.0 seconds = 248.600 FPS

```
](*,)

---

### Post by utherwayn on 2006-07-07
I honestly don't know how to thank you for your help fitzman49

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5879 (8.26.18)

---

### Post by caish5 on 2006-07-07
@Steven_B

Still no joy. All fatal again!!!
Same error ..no screns found.

Oh god i wish this laptop had an nvidia. My desktop is a breeze to setup even with dual monitors!

---

### Post by Steven_B on 2006-07-07
@caish5
Does your "ServerLayout" section have a line:
```
Screen         "aticonfig-Screen[0]" 0 0
```

Also, you might want to check that the computer can see the card:
```
lspci | grep ATI
```  Make sure there is a line about a VGA compatible controller.
Sorry if this doesn't help.

---

### Post by caish5 on 2006-07-07
Affirmative on both counts but still fails :(

---

### Post by TGArcher on 2006-07-07
I followed the instructions to the letter posted in the Ubuntu Installation guide (basically the same here). Everything seemed to work. Infact it was perfect, exept that when I rebooted and tried to see if it worked, it still said:


display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


I also used the command sudo sh ati-driver-installer-8.26.18-x86.run to use the graphical installer. they both worked perfect, but it still says the same stuff! What am I not doing!!? I'm running a Compaq Presario V2000 with an ATI 200M. IT just drives me up the wall  having everything go right, even having the ATI Controller, and all your labor seems to come void.

---

### Post by d-E-a-D on 2006-07-07
8.26 works bad or doesn't work with 200M, install 8.24 and you will get it running perfect.
Cumps

---

### Post by Dubbayoo on 2006-07-07
I cannot build this either. When I try to 'sudo module-assistant build,install fglrx I get an error.

--------
/usr/bin/make  -f debian/rules clean
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
# select which makefile to use.
rm -f /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/Makefile || true
cd /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x ; \
	ln -s Makefile.kbuild Makefile ; \
	cd .. ; \

if [ -e patch-stamp ]; then \
	   dpatch deapply-all ; \
	   rm -rf patch-stamp debian/patched ; \
	fi   
if [ -f /usr/src/modules/fglrx-kernel/debian/control.template ]; then \
		cp  /usr/src/modules/fglrx-kernel/debian/control.template /usr/src/modules/fglrx-kernel/debian/control; \
	fi
dh_testroot
rm -f build-stamp configure-stamp
/usr/bin/make clean SYSSRC=/usr/src/linux -C /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x -f Makefile "KDIR=/usr/src/linux-headers-$i"
make[2]: Entering directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
echo "ROOT_CMD = "
ROOT_CMD = 
/usr/bin/make  -f debian/rules binary_modules
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
# select which makefile to use.
rm -f /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/Makefile || true
cd /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x ; \
	ln -s Makefile.kbuild Makefile ; \
	cd .. ; \

#nothing here anymore
touch configure-stamp
if [ -f /usr/src/modules/fglrx-kernel/debian/control.template ]; then \
		cp  /usr/src/modules/fglrx-kernel/debian/control.template /usr/src/modules/fglrx-kernel/debian/control; \
	fi
dh_testdir
dh_testroot
PATCHLEVEL = 6 
Kernel compiler version : 4.0.3
Detected compiler version : 4.0.3
Using compiler gcc-4.0 version 4.0.3
touch /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/gcc-check
touch /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/cc-sanity-check
## Main Make ##
IGNORE_CC_MISMATCH=1 CC="gcc-4.0"  /usr/bin/make -C /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x -f Makefile SYSSRC=/usr/src/linux  "KDIR=/usr/src/linux-headers-$i" KBUILD_PARAMS="-C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x"
make[2]: Entering directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[2]: **Makefile: No such file or directory**
make[2]: *** No rule to make target `Makefile'.  Stop.
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
make: *** [kdist_image] Error 2
----------------


steve@ubu:~$ ls -l /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/
total 0
-rw-r--r-- 1 root root  0 2006-07-07 19:07 cc-sanity-check
-rw-r--r-- 1 root root  0 2006-07-07 19:07 gcc-check
lrwxrwxrwx 1 root root 15 2006-07-07 19:07 Makefile -> Makefile.kbuild

--------------------


I see the Makefile is looking for something that isn't there, **Makefile.kbuild**. Where does this file come from?

---

### Post by TGArcher on 2006-07-08
> **d-E-a-D said:**
> 8.26 works bad or doesn't work with 200M, install 8.24 and you will get it running perfect.
Cumps


But the guy who wrote this tread got it working with no problems!

---

### Post by EReckase on 2006-07-08
> **TGArcher said:**
> But the guy who wrote this tread got it working with no problems!

The fact of the matter is, if you have a 200M card, you're much more likely to have success with the 8.24.8 drivers than any other version so far released (especially with those pesky HP Pavilions) - and the process to install them is fairly well documented.  Given that the performance of the 200M isn't all that spectacular to begin with (1200 fps with glxgears?  fergeddaboudit.) new ATI drivers aren't *really* going to make a humongous difference in the card's capabilities.

If I were to double my framerate with the new drivers, I'd be interested.  Otherwise, I've given up on trying with the latest & greatest.  At a certain point, newest isn't necessarily best.

](*,)

---

### Post by TGArcher on 2006-07-08
> **d-E-a-D said:**
> 8.26 works bad or doesn't work with 200M, install 8.24 and you will get it running perfect.
Cumps

Hold on, I found something. I still get the same thing when I do fglrxinfo, But this is what my xorg.conf file looks like (well, at least the part with the driver):

Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x768"
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



It looks all correct, but why does it act like I dont have a thing working?
](*,)

---

### Post by Zifnab on 2006-07-08
I installed 64-bit Dapper the other day, so I had a fairly "clean" system to try out this install method on for my Radeon 9800 Pro, and it worked perfectly.

'Bout damn time something went my way... I switched to Ubuntu for no other reason than that Gentoo was giving me a helluva time trying to get ATI's crappy drivers to work.

---

### Post by FabreNZ on 2006-07-08
I just installed it on my Toshiba A100 with a Mobility X1300.  I opened Neverball to test it, and found that it was running at about 1 frame per second (down from solid 60).  I ran "glxinfo | grep rendering", and it says direct rendering is now disabled.

I guess I'll have to try to get back to 8.25.18 like others have done.

EDIT: I went through the process again, and it worked this time.  I have no idea why, I'm just glad I have my hardware acceleration back.

---

### Post by krazykirk on 2006-07-08
Wow! It worked! Now I should be able to use 3d! =D

---

### Post by Steven_B on 2006-07-08
@TGArcher
From what I can see of the file, you are missing a monitor with the line "Identifier "aticonfig-Monitor[0]"".  Also, check that the server section is using the "aticonfig-Screen[0]".

I have an Xpress 200, and it seems to work fine here, except that it might be causing the "white screen of death".

---

### Post by btr on 2006-07-08
When i try to install this Deb. package (sudo dpkg -i fglrx-control_8.26.18-1_i386.deb) i get this error (** (process:8559): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed) Can anyone help?

---

### Post by TGArcher on 2006-07-08
> **EReckase said:**
> The fact of the matter is, if you have a 200M card, you're much more likely to have success with the 8.24.8 drivers than any other version so far released (especially with those pesky HP Pavilions) - and the process to install them is fairly well documented.  Given that the performance of the 200M isn't all that spectacular to begin with (1200 fps with glxgears?  fergeddaboudit.) new ATI drivers aren't *really* going to make a humongous difference in the card's capabilities.

If I were to double my framerate with the new drivers, I'd be interested.  Otherwise, I've given up on trying with the latest & greatest.  At a certain point, newest isn't necessarily best.

](*,)

So I tried the 8.24.8 driver. I couldn't install it cause I get this

Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 7.0.0

Detected version of X does not have a matching 'x700' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x410        XFree86 4.1.x
    x420        XFree86 4.2.x
    x430        XFree86 4.3.x
    x680        X.Org 6.8.x
    x690        X.Org 6.9.x

I am running Xorg 7.0.0 though! and if I would have known that I would have this troble with Gentoo and now with Ubuntu, I wouldn't have gotten this laptop. Personally, I HATE ATI because for this very reason. so can neone tell me the best laptop to get to run Linux?

---

### Post by Dubbayoo on 2006-07-08
Okay I fixed my previous error but now i'm getting another one

steve@ubu:~/tmp$ **fglrxinfo**
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
------------------------------------------

Truncated **/var/log/Xorg.log**

(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 8500 (R200 514C)" (Chipset = 0x514c)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x013a)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xf5000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 8500
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R200
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
d[B]rmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection[/B]
(II) fglrx(0): Video RAM override, using 131072 kB instead of 131072 kB
(**) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0):  Display1: Failed to get EDID information.
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 19 modes found for primary display.
(--) fglrx(0): Virtual size is 1400x1050 (pitch 0)
(II) fglrx(0): UMM Bus area:     0xe07ad000 (size=0x07853000)
(II) fglrx(0): UMM area:     0xe07ad000 (size=0x07853000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
[B]drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *[/B]


----------------------------
[B]
module section from xorg.conf[/B]


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

-------------------------

This is a Radeon 8500. I've had the previous working most of the time except the libGL thing. Some help please?

---

### Post by Dubbayoo on 2006-07-08
nm, it works if I replace libGL.so.1.2

---

### Post by Jolly Roger on 2006-07-09
Great guide. Worked awesomely for me. Now I've got Ubuntu in all of it's 1680x1050 resolution glory.

---

### Post by eternalsword on 2006-07-10
I have an x300 with 128MB of memory.  I got fglrx 8.26.18 up and running, but fireglcontrol shows only 32MB of video card memory.  How would I go about utilizing the full 128MB, or is fireglcontrol not outputting the correct value?

---

### Post by IronWolve on 2006-07-10
Took me days, until I found that I had to blacklist the module.

Not common knowledge that ubuntu loads these legacy modules..... Bad!

---

### Post by almahtar on 2006-07-10
> **IronWolve said:**
> Took me days, until I found that I had to blacklist the module.

Not common knowledge that ubuntu loads these legacy modules..... Bad!
Same here!  I had no idea that was important.  I just now got the 8.26.18 working for the first time.  Yay blacklisting!!!

Next step: aiglx.

---

### Post by btr on 2006-07-10
HELP ME PLEASE! I cannot seem to get these drivers to work. I have been on Linux for about a week, so i'm a noob. I have tried every how-to i have come across.
I am trying to install them on a freshley installed and updated Ubuntu. AGP X800GTO

Here is my xorg.conf. Let me know if you need anything else.


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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Driver      "ati"
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
	Device     "ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
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

### Post by almahtar on 2006-07-11
> **btr said:**
> HELP ME PLEASE! I cannot seem to get these drivers to work. I have been on Linux for about a week, so i'm a noob. I have tried every how-to i have come across.
I am trying to install them on a freshley installed and updated Ubuntu. AGP X800GTO

Here is my xorg.conf. Let me know if you need anything else.


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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Driver      "ati"
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
	Device     "ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
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

Heya.  Could you tell me what output you get when you type:
```
 cat /var/log/Xorg.0.log | grep fglrx 
```
That'd help a lot.  If you have time I wouldn't mind seeing the output of ```
 dmesg | grep fglrx 
```

If the output scrolls by too fast, you can put the text ```
 | less 
``` after any of those commands and it'll let you use the arrow keys to scroll up and down the output.  For example, "cat /var/log/Xorg.0.log | grep fglrx | less"

Best of luck.  If you have questions feel free to ask.

---

### Post by btr on 2006-07-11
Here is the first one.


btr@btr-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

btr@btr-desktop:~$ # ls -la *GL*
btr@btr-desktop:~$ sudo # ls -la *GL*
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
btr@btr-desktop:~$ # cd /usr/X11R6/lib
btr@btr-desktop:~$ cat /var/log/Xorg.0.log | grep fglrx
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x81db800
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON X800 GTO (R430 554F)" (Chipset = 0x554f)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x1600)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xff5f0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.8
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2003, ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R430
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR3
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: PTS  Model: 309  Serial#: 9026
(II) fglrx(0): Year: 2003  Week: 36
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) fglrx(0): Gamma: 2.98
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.618 redY: 0.349   greenX: 0.280 greenY: 0.605
(II) fglrx(0): blueX: 0.152 blueY: 0.063   whiteX: 0.281 whiteY: 0.310
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 100  vid: 26693
(II) fglrx(0): #4: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #5: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) fglrx(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  320 x 240 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1068 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) fglrx(0): Serial No: FBUD39009026U
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 398/493MHz @ 0Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 43 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1068
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.29  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "960x720": 55.9 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x720"   55.86  960 1008 1104 1248  720 721 724 746
(**) fglrx(0): *Mode "864x648": 45.1 MHz (scaled from 0.0 MHz), 40.2 kHz, 60.0 Hz
(II) fglrx(0): Modeline "864x648"   45.08  864 904 992 1120  648 649 652 671 +hsync +vsync
(**) fglrx(0): *Mode "856x480": 31.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "856x480"   31.73  856 872 960 1064  480 481 484 497
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.61  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.18  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.72  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "704x480": 26.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "704x480"   26.24  704 720 792 880  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.41  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1068
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.29  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "960x720": 55.9 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x720"   55.86  960 1008 1104 1248  720 721 724 746
(**) fglrx(0): *Mode "864x648": 45.1 MHz (scaled from 0.0 MHz), 40.2 kHz, 60.0 Hz
(II) fglrx(0): Modeline "864x648"   45.08  864 904 992 1120  648 649 652 671 +hsync +vsync
(**) fglrx(0): *Mode "856x480": 31.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "856x480"   31.73  856 872 960 1064  480 481 484 497
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.61  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.18  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.72  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "704x480": 26.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "704x480"   26.24  704 720 792 880  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.41  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (320, 240) mm
(--) fglrx(0): DPI set to (101, 108)
(==) fglrx(0): NoAccel = NO
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
(==) fglrx(0): cpuSpeedMHz: 0x000008e0
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb6fa9000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.26.18
(II) fglrx(0):     Date: Jun 22 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.15-25-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb6fa9000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 7163

Here is the second.

[17179602.964000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179602.968000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179602.968000] [fglrx] module loaded - fglrx 8.26.18 [Jun 22 2006] on minor 0[17179604.168000] [fglrx] Internal AGP is not supported in 2.6 kernel.
[17179604.168000] [fglrx:firegl_unlock] *ERROR* Process 4418 using kernel context 0

---

### Post by schambee on 2006-07-11
just wanted to say that this was the first time for me to install a fglrx driver without any problems. awesome howto! thanx a lot.

---

### Post by Carlos Araujo on 2006-07-11
carlos@carlos-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.5879 (8.26.18)


:confused:

---

### Post by Carlos Araujo on 2006-07-11
> **Carlos Araujo said:**
> carlos@carlos-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.5879 (8.26.18)


:confused:

ATI RADEON 1900xt

---

### Post by operationsone on 2006-07-11
Ok, so I got many problems with ATI drivers, other versions used to hard lock some time or another. Let's hope this one does not. At first I also had the infamous Mesa issue. Here's how i got over it:

First I blacklisted the fglrx driver:

blacklist old fglrx module from linux-restricted-modules

sudo gedit /etc/default/linux-restricted-modules-common

Edit DISABLED_MODULES to include fglrx
File: /etc/default/linux-restricted-modules-common

DISABLED_MODULES="fglrx"

then i removed every single linux-restricted-modules-... that i had on my system.

then do a sudo dpkg-reconfigure xserver-xorg and choose the ati driver. Reboot now.

follow the procedure explained here:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually")

Don't forget the sudo aticonfig --initial after compiling the kernel modules.

Reboot now.

Try fglrxinfo and confirm that it installed.

Play some tuxkart to make sure it's working with textures, decent speed, etc

That's it.

Hope this helps someone out there, installing video drivers is just ](*,)

---

### Post by btr on 2006-07-12
Ok mine works now? All i did was turn the computer off for about 30 minutes. If i can't get these drivers to work right i'm going to get an Nvidia card.:mrgreen: 

Now i get,

btr@btr-desktop:~$ cat /var/log/Xorg.0.log | grep fglrx
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x81db800
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON X800 GTO (R430 554F)" (Chipset = 0x554f)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x1600)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xff5f0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.8
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2003, ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R430
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR3
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: PTS  Model: 309  Serial#: 9026
(II) fglrx(0): Year: 2003  Week: 36
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) fglrx(0): Gamma: 2.98
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.618 redY: 0.349   greenX: 0.280 greenY: 0.605
(II) fglrx(0): blueX: 0.152 blueY: 0.063   whiteX: 0.281 whiteY: 0.310
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 100  vid: 26693
(II) fglrx(0): #4: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #5: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) fglrx(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  320 x 240 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1068 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) fglrx(0): Serial No: FBUD39009026U
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 398/493MHz @ 0Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 43 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1068
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.29  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "960x720": 55.9 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x720"   55.86  960 1008 1104 1248  720 721 724 746
(**) fglrx(0): *Mode "864x648": 45.1 MHz (scaled from 0.0 MHz), 40.2 kHz, 60.0 Hz
(II) fglrx(0): Modeline "864x648"   45.08  864 904 992 1120  648 649 652 671 +hsync +vsync
(**) fglrx(0): *Mode "856x480": 31.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "856x480"   31.73  856 872 960 1064  480 481 484 497
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.61  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.18  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.72  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "704x480": 26.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "704x480"   26.24  704 720 792 880  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.41  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1068
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.29  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "960x720": 55.9 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x720"   55.86  960 1008 1104 1248  720 721 724 746
(**) fglrx(0): *Mode "864x648": 45.1 MHz (scaled from 0.0 MHz), 40.2 kHz, 60.0 Hz
(II) fglrx(0): Modeline "864x648"   45.08  864 904 992 1120  648 649 652 671 +hsync +vsync
(**) fglrx(0): *Mode "856x480": 31.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "856x480"   31.73  856 872 960 1064  480 481 484 497
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.61  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.18  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.72  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "704x480": 26.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "704x480"   26.24  704 720 792 880  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.41  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (320, 240) mm
(--) fglrx(0): DPI set to (101, 108)
(==) fglrx(0): NoAccel = NO
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
(==) fglrx(0): cpuSpeedMHz: 0x000008e0
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb71c7000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.26.18
(II) fglrx(0):     Date: Jun 22 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.15-25-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [agp] Mode=0x1f00421b bridge: 0x10de/0x00e1
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f00431a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xf8000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f004312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x00701000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(II) fglrx(0): Interrupt handler installed at IRQ 201.
(II) fglrx(0): Exposed events to the /proc interface
and

btr@btr-desktop:~$ dmesg | grep fglrx
[17179603.792000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179603.792000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179603.792000] [fglrx] module loaded - fglrx 8.26.18 [Jun 22 2006] on minor 0[17179604.976000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179604.976000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179604.976000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[17179604.980000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179604.984000] [fglrx] total      GART = 67108864
[17179604.984000] [fglrx] free       GART = 51113984
[17179604.984000] [fglrx] max single GART = 51113984
[17179604.984000] [fglrx] total      LFB  = 126873600
[17179604.984000] [fglrx] free       LFB  = 116387840
[17179604.984000] [fglrx] max single LFB  = 116387840
[17179604.984000] [fglrx] total      Inv  = 134217728
[17179604.984000] [fglrx] free       Inv  = 134217728
[17179604.984000] [fglrx] max single Inv  = 134217728
[17179604.984000] [fglrx] total      TIM  = 0

I am lost!

---

### Post by btr on 2006-07-12
When i run glxgears i get this

btr@btr-desktop:~$ glxgears -printfps
41602 frames in 5.0 seconds = 8320.215 FPS

---

### Post by btr on 2006-07-12
Ok i just ran Update manager and restarted. Now the drivers are broke again.:confused:

---

### Post by operationsone on 2006-07-12
> **btr said:**
> Ok i just ran Update manager and restarted. Now the drivers are broke again.:confused:

you probably need to recompile the kernel modules again, because the last update had a new kernel.

on a side note, I just gave up trying to make the propietary drivers work..they work 1 time and then stop, hard lock, screw everything up, etc..it's just not worth it if you don't really need it.

---

### Post by btr on 2006-07-12
> **operationsone said:**
> you probably need to recompile the kernel modules again, because the last update had a new kernel.

on a side note, I just gave up trying to make the propietary drivers work..they work 1 time and then stop, hard lock, screw everything up, etc..it's just not worth it if you don't really need it.

I just recompiled the kernel, they work for now.:mrgreen:  The question is, for how long?

---

### Post by vitesse on 2006-07-12
I ppl I read the entire thread to find this answer:

Is the a way to install the ati driver in a fresh installation of dapper without internet connection?

please help me I read 14 pages looking for an answer.

TIA

---

### Post by bschmiduk on 2006-07-12
Hi all.  I'm a Linux noob (but have been doing computers since punchcards were the height of tech).  Used the Ubuntu LiveCD for 2 weeks, and am now dual-booting with XP.

I went through the arcane pain at the start of this thread to get my Ati X800 pro card to work.  And like others, broke them again with the latest kernel update.

I went through all that arcane pain again, and now they work again.  Would one of the Linux gurus out there go through the steps to *just* recompile the kernel?  I just barely know what I am doing.

Thanks.

---

### Post by TrinitronX on 2006-07-12
I've found a bug that's just gotten worse in the new drivers.
It's been showing up both before and after the kernel update, and I've downgraded the drivers to test if they are indeed the cause... and I've found that yes, they are.

Here's the problem:
I've got 2 monitors hooked up into my Radeon 9800pro.  One's a widescreen LCD using the DVI input, the other's a CRT using the analog (VGA) input.  I think it is caused by the differing resolutions.  The LCD is 1440x900 and the CRT is set at 2048x1024.  The problem shows up at the gdm login screen, and with previous drivers, only happened on the CRT monitor.

Since a picture is worth a thousand words, here are some images showing what's going on:
LCD with 8.25.18 drivers
[[IMG]http://img76.imageshack.us/img76/5048/ati82518lcd8ne.th.jpg[/IMG]](http://img76.imageshack.us/img76/5048/ati82518lcd8ne.jpg)

CRT with 8.25.18 drivers
[[IMG]http://img76.imageshack.us/img76/6469/ati82518crt0gz.th.jpg[/IMG]](http://img76.imageshack.us/img76/6469/ati82518crt0gz.jpg)

LCD with 8.26.18 drivers
[[IMG]http://img100.imageshack.us/img100/9193/ati82618lcd5tw.th.jpg[/IMG]](http://img100.imageshack.us/img100/9193/ati82618lcd5tw.jpg)

CRT with 8.26.18 drivers
[[IMG]http://img139.imageshack.us/img139/5639/ati82618crt9nk.th.jpg[/IMG]](http://img139.imageshack.us/img139/5639/ati82618crt9nk.jpg)

Judging from the following image, I'm going to guess that the bar at the bottom of the screen is whatever happens to be saved in RAM at the moment.  Before restarting and taking this picture, I was browsing ATI's website. In the enlarged image, look at the stuff in the 'garbage bar' :p
[[IMG]http://img92.imageshack.us/img92/8241/vramcontentsoffscreen2zx.th.jpg[/IMG]](http://img92.imageshack.us/img92/8241/vramcontentsoffscreen2zx.jpg)

Well... at least now they've made sure the video output to both screens is the same... now only if they'd figure out how to deal with different resolutions without dumping garbage onto the screen :p

---

### Post by operationsone on 2006-07-12
> I just recompiled the kernel, they work for now. The question is, for how long?

exactly :-D 

@ TrinitronX :

your last pic is just hilarious, those fglrx drivers have some serious problems :-D :-D 

Right now I'm using the good 'old "ati" drivers :D no crash or anything, but i dont get anywhere near decent speeds in 3d apps.

---

### Post by fitzman49 on 2006-07-13
@vitesse

You will need to download the ati driver package posted in the first post of this thread and make sure you have the correct modules installed before you do anything.  Also make sure you have the kernel headers downloaded for the specific kernel you are using.  Just do a:

```
uname -a
```

This will tell the specific kernel you are using. All of these except the ati driver package can be downloaded through synaptic. Once all those are downloaded the installation can be done offline.

---

### Post by fitzman49 on 2006-07-13
> **bschmiduk said:**
> Hi all.  I'm a Linux noob (but have been doing computers since punchcards were the height of tech).  Used the Ubuntu LiveCD for 2 weeks, and am now dual-booting with XP.

I went through the arcane pain at the start of this thread to get my Ati X800 pro card to work.  And like others, broke them again with the latest kernel update.

I went through all that arcane pain again, and now they work again.  Would one of the Linux gurus out there go through the steps to *just* recompile the kernel?  I just barely know what I am doing.

Thanks.

I am no guru by far but do this to compile the kernel with the fglrx drivers:

```
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```

If you 'just' want to recompile the kernel then remove the ",install fglrx" part and the will compile the kernel with no installation of anything.  I am also in the process of building a script that will do the whole install without you having to do anything.  Hopefully I can juggle it around work and play:-k

---

### Post by whatever on 2006-07-13
> **fitzman49 said:**
> I am no guru by far but do this to compile the kernel with the fglrx drivers
this does only compile the fglrx module, not the kernel.
there is no need to recompile the whole kernel...

the "prepare,update" part ensures that you habe matching kernel headers installed.
the "build,install" thing builds the kernel module, creates a .deb file for it and installs this file.

---

### Post by mikewilson on 2006-07-13
Many many thanks -- my XPress 200 now works as it should. That was beautifully explained and straightforward to follow. Now if you could just do the same thing for my wireless card...

---

### Post by vitesse on 2006-07-13
> **fitzman49 said:**
> @vitesse

You will need to download the ati driver package posted in the first post of this thread and make sure you have the correct modules installed before you do anything.  Also make sure you have the kernel headers downloaded for the specific kernel you are using.  Just do a:

```
uname -a
```

This will tell the specific kernel you are using. All of these except the ati driver package can be downloaded through synaptic. Once all those are downloaded the installation can be done offline.
Thanks fitzman49's 

But how I can download if I dont have internet connection?. 

Can I download all the packages needed, put it in a local dir and then install from there?

I'm just imaginating this I don't know how to do it. I only have internet connection at work. I plan to download and burn everything I need, then install at my house.

Can you help me on this?

TIA

---

### Post by fitzman49 on 2006-07-13
yes you could but it would be very time consuming.  make sure you get all the debs needed before you start the install and the kernel headers.  then get the ati driver package and throw that in a directory with all the debs.  then just follow the guide and it should work.:-k

---

### Post by eternalsword on 2006-07-14
I have an ati x300 with 128MB, but fireglcontrolpanel only lists 32MB.  How can I utilize all the memory?  

```

:~$ cat /var/log/Xorg.0.log | grep fglrx
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x81dbb98
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON X300/X550 (RV370 5B60)" (Chipset = 0x5b60)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0602)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xec000000
(--) fglrx(0): MMIO registers at 0xefde0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RV370
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V380
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(--) fglrx(0): VideoRAM: 32768 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) fglrx(0): Connected Display1: DFP on internal TMDS
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: DEL  Model: 4015  Serial#: 810561601
(II) fglrx(0): Year: 2006  Week: 17
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.328   greenX: 0.300 greenY: 0.600(II) fglrx(0): blueX: 0.149 blueY: 0.060   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Serial No: 6418064P0P0A
(II) fglrx(0): Monitor name: DELL 1907FP
(II) fglrx(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 324/297MHz @ 50Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 35 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.77  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "960x720": 55.9 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x720"   55.86  960 1008 1104 1248  720 721 724 746
(**) fglrx(0): *Mode "864x648": 45.1 MHz (scaled from 0.0 MHz), 40.2 kHz, 60.0 Hz
(II) fglrx(0): Modeline "864x648"   45.08  864 904 992 1120  648 649 652 671 +hsync +vsync
(**) fglrx(0): *Mode "856x480": 31.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "856x480"   31.73  856 872 960 1064  480 481 484 497
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.72  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "704x480": 26.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "704x480"   26.24  704 720 792 880  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.77  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "960x720": 55.9 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x720"   55.86  960 1008 1104 1248  720 721 724 746
(**) fglrx(0): *Mode "864x648": 45.1 MHz (scaled from 0.0 MHz), 40.2 kHz, 60.0 Hz
(II) fglrx(0): Modeline "864x648"   45.08  864 904 992 1120  648 649 652 671 +hsync +vsync
(**) fglrx(0): *Mode "856x480": 31.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "856x480"   31.73  856 872 960 1064  480 481 484 497
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.72  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "704x480": 26.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "704x480"   26.24  704 720 792 880  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (380, 300) mm
(--) fglrx(0): DPI set to (85, 86)
(==) fglrx(0): NoAccel = NO
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
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): cpuSpeedMHz: 0x00000ae9
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xec701000 (size=0x018df000)
(II) fglrx(0): UMM area:     0xec701000 (size=0x018df000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7ee8000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.26.18
(II) fglrx(0):     Date: Jun 22 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.15-26-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [pcie] 131072 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xec000000 FBMappedSize: 0x00701000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(II) fglrx(0): Interrupt handler installed at IRQ 169.
(II) fglrx(0): Exposed events to the /proc interface


```

---

### Post by koshari on 2006-07-14
check this thread

 Ubuntu 6.06 - fglrx just recently went very wrong

:~$ ooffice -writer %U [fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS 
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI

The latest ATI drivers are broken with r200 cards it seems.

i’m just using the older drivers for now... hopefully they’ll fix it in the next release or something.

i can upload the file if you need it.. its for the version before this one.. that should fix you up

[http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2)

---

### Post by neikous on 2006-07-14
thanks fitzman. it's teeps by the way. see ya

---

### Post by disciple on 2006-07-16
worked for me, Compaq v2000z  w Xpress 200m  YAY!!
lol

good job on the howto

---

### Post by ciaka on 2006-07-17
Thanks Fitzman.  Worked flawlessly first time.

---

### Post by doog on 2006-07-17
People really need to specify two things before they say this "works".

1) Are you only talking about 2D support or are you including full(DRI ) 3D support is working?

2) Does your laptop have any onboard video memory or are you using just shared memory?

There are people saying that the new driver works but there's no way it is if they are talking about full 3D/DRI suport and are using only Sideport/onboard video memory.

In a few cases you can get the driver to "work" if both 128MB of onboard and 128MB of shared memory are used, but in most cases, only 100% UMA/shared video memory will work with the Xpress 200M and the 8.26.18 driver. This has been broken since 8.13.6 driver 1 year ago but once worked in the 8.13.4 driver.

So please specify what is 'really' working when you say it works. And for those who have already posted that it works, could you please update your posts so that people don't waste there time attempting to install this thinking that they'll get full 3D support working again? Thanks.

---

### Post by Kilz on 2006-07-17
Just a note, I wanted to update my kernel and drivers because I was still using 8.24.8 because of the way the 8.25.18 drivers never shut down correctly because I had a Radon x200. 
At about the 4th try and glxgears not working. I noticed that when I tried to install xorg-driver-fglrx_8.26.18-1_amd64.deb I noticed that there was an error of not being able to replace the libGL.so.1.2 in /usrlib and /usr/lib32. I deleted the libs then and installed the package without errors. Then acceleration worked.

---

### Post by c0ncept on 2006-07-18
> **fitzman49 said:**
> ...
Install .deb packages:

```
sudo dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb 
sudo dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb 
sudo dpkg -i fglrx-control_8.26.18-1_i386.deb
```

I'm brand new to installing stuff in Ubuntu and trying to understand the command lines, and I'm trying to install these new drivers for my ATI Radeon 9600XT.  I've followed along until this step and I get the following error in the terminal:

account@comp2:~$ sudo dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb 
dpkg: error processing xorg-driver-fglrx_8.26.18-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.26.18-1_i386.deb


I don't really understand what that means, can anyone help so I can proceed to finish this installation?

---

### Post by fitzman49 on 2006-07-19
> **c0ncept said:**
> I'm brand new to installing stuff in Ubuntu and trying to understand the command lines, and I'm trying to install these new drivers for my ATI Radeon 9600XT.  I've followed along until this step and I get the following error in the terminal:

account@comp2:~$ sudo dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb 
dpkg: error processing xorg-driver-fglrx_8.26.18-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.26.18-1_i386.deb


I don't really understand what that means, can anyone help so I can proceed to finish this installation?

Make sure when your using the console you need to be in the directory where you are storing the .debs before you can install something or dpkg will not find the downloaded files.  It should say what the present working directory you are in on the title bar of the console window. Also if you are using the 64 bit version the names will differ so if you are copying and pasting the commands they will not work. Seems to be the only things I can think of at the moment.

---

### Post by c0ncept on 2006-07-19
> **fitzman49 said:**
> Make sure when your using the console you need to be in the directory where you are storing the .debs before you can install something or dpkg will not find the downloaded files.  It should say what the present working directory you are in on the title bar of the console window. Also if you are using the 64 bit version the names will differ so if you are copying and pasting the commands they will not work. Seems to be the only things I can think of at the moment.

```
account@comp2:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5879 (8.26.18)
```

Thanks for the help, the rest of the steps worked like a charm!  fitzman ftw! :D

---

### Post by mrbaz on 2006-07-19
I've been trying this over and over and over again.  I even did a fresh install of Dapper thinking it would help.
The first thing I did after I installed Dapper was to blacklist fglrx.

I went through the whole process, but now fglrxinfo shows I am still using the mesa drivers or something.

glxgears -printfps shows 291fps in 5 seconds, so yeah...still not working.

This is on a Dell 600m, Radeon 9000.

Redid it.
Now I get this:
```

fglrxinfo
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
[fglrx] API ERROR: could not register entrypoint for DisableVariantClientStateEX T
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
[fglrx] API ERROR: could not register entrypoint for GetInvariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantFloatvEXT
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
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectf vATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjecti vATI
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
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvA RB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvA RB
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
[fglrx] API ERROR: could not register entrypoint for SetFragmentShaderConstantAT I
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
[fglrx] API ERROR: could not register entrypoint for BeginDefineVisibilityQueryA TI
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
[fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivE XT
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentPar ameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT

```

I even did 'dpkg-reconfigure xserver-xorg' like some have suggested.  I let it autoselect my vid card, which it found, and selected the ati driver.

I'll redo the reconfigure and this time select fglrx and then recompile/install the drivers again.
update; nope, still same thing as all that code above.

---

### Post by Awalton on 2006-07-20
> **koshari said:**
> check this thread

 Ubuntu 6.06 - fglrx just recently went very wrong

:~$ ooffice -writer %U [fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS 
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI

The latest ATI drivers are broken with r200 cards it seems.

i’m just using the older drivers for now... hopefully they’ll fix it in the next release or something.

i can upload the file if you need it.. its for the version before this one.. that should fix you up

[http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2)


Thanks so much for that library, my FireGL card now has 3D Accelleration, weeee. Off to XGL ;)

---

### Post by grimmc on 2006-07-20
@fitzman49: Thanks for the great guide! Just did a clean install of Ubuntu 6.06 the other day. Aside from the whole DNS lookups failing - that's a story for another day :mrgreen: - everything else just worked straight out of the box. I basically followed your guide step by step and in no time I was in OpenGL accelerated heaven :D

---

### Post by alonz on 2006-07-21
Help i'm new to linux i tried everything but still can't get fglrx driver to work 

i have Ibm R51 with Radeon Mobility 9000 with kubuntu dapper

fglrxinfo give:
Error: unable to open display :0

my xorg.conf is:


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
	InputDevice    "Synaptics Touchpad"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver      "ati"
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
	Device     "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768"
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


any ideas ?

---

### Post by dillanlaughlin on 2006-07-23
I'm having issues getting the fglrx drivers running on my machine. I'm following all the steps exactly as they are written on an Asus barebones system with the Xpress 200 on-board video. I've also tried the instructions on other sites, even ATI, but without any good results. I keep getting an error message saying "Failed to start the X server (your graphical interface)....."

---

### Post by sp4zzj4zz on 2006-07-23
After nearly 3 days of messing with this silly issue...

FINALLY...

```
sp4zz@light-node:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.5879 (8.26.18)
```
No more mesa3d crap! 

Being a convert from XP to (K)Ubuntu, I can't thank you enough for the information provided here.

The steps I took were this...

(1) Fresh install of Dapper
(2) Update
(3) Blacklist fglrx
(4) Followed all steps in the first post

Now to figure out how to get VGA out to my LCDTV in 1360x1024 resolution...

---

### Post by chadk on 2006-07-23
Every time I get a new kernel update my system reverts back to MESA and I have to figure out how to outsmart the system and get fglrx working again.  Well this last time I had compiz installed and decided since my kernel update broke fglrx again I'd just remove compiz.  I'm lost now.  I have removed compiz and xgl completely and have followed 2-3 tutorials on how to install fglrx and none of them are working.  No errors reported but when I reboot I'm still in MESA.

```
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X800 SE (R420 JJ)"
	Driver      "fglrx"
	VideoRam    262144
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection
```

---

### Post by rmjb on 2006-07-23
This worked for me, no probs. Using Ubuntu 32bit, have kernel 2.6.15-26-386 and an X800 GTO according to ATI Control.

- rmjb

---

### Post by dillanlaughlin on 2006-07-23
fitzman 49 I have followed every one of your steps and reccomendations that are strewn about this thread and I'm going nuts here. 

Here is my xorg.conf:

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
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	VideoRam	128000
	Option		"UseFBDev"		"true"
	Option 		"VideoOverlay" 		"on" 
	Option 		"OpenGLOverlay" 	"off"


EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

I am using the Xpress 200 that is built onto my Asus mobo.

Please tell me if you think I made some sort of mistake ](*,)  or if you think the ATI driver may be faulty.

---

### Post by azumi on 2006-07-24
wrks fine 4 me, im a beginner in ubuntu, thx 4 this nice guide!

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5879 (8.26.18)

Toshiba Satellite 
resolution is - 1280x800 60hz

---

### Post by Alyus on 2006-07-24
I have been having a terrible time trying to get the 3d accelleration to work with my system.  I had been trying with breezy and decided to try upgrading (via clean install) to dapper hoping my problem would be magically fixed. However it wasn't. I have a somewhat different system (set up as a home theater pc) and it is attached to my hdtv via svideo connection.  Any help would be greatly appreciated.

I appologize I don't know how to put in those cool little "code" boxes so big text files are attached.

-System Details:-
Radeon 9800 pro Hooked to tv via svideo
Asus K8n-e deluxe MB latest bios installed
Dual booting w/win2k

-dmesg | grep fglrx-
[17179598.724000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179598.724000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179598.724000] [fglrx] module loaded - fglrx 8.26.18 [Jun 22 2006] on minor 0
[17179602.416000] [fglrx] Internal AGP is not supported in 2.6 kernel.
[17179602.416000] [fglrx:firegl_unlock] *ERROR* Process 4877 using kernel context 0

-glxinfo-
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

Xorg.conf = xorg.txt
xorg.0.log & kern.log are in archive.zip

Thank You very much in advance!!

Alyus

---

### Post by linux-nOOb on 2006-07-24
These drivers have been out for nearly a month now....why aren't they in the repositories yet?

linux-nOOb

---

### Post by rmjb on 2006-07-24
> **rmjb said:**
> This worked for me, no probs. Using Ubuntu 32bit, have kernel 2.6.15-26-386 and an X800 GTO according to ATI Control.

- rmjb

My bad, I'm using this the next day and glxinfo says it's Mesa3D :( 

- rmjb

---

### Post by Jaxilian on 2006-07-25
This howto doesn't work for me and my ATi Radeon 9000

see other post: [http://www.ubuntuforums.org/showthread.php?t=222562](http://www.ubuntuforums.org/showthread.php?t=222562)

I have yet to see a ATi driver howto that works. It's the only thing that keep me from switching over from Windows.
If I don't ge this to work in a few days I am swtiching back cause I can't keep messing around with it too long. I need a functioning computer so I can work on it.

---

### Post by rmjb on 2006-07-25
What functionality do you need from Ubuntu that the fglrx driver provides that keeps you from having a functioning computer?

- rmjb

---

### Post by Jaxilian on 2006-07-25
> **rmjb said:**
> What functionality do you need from Ubuntu that the fglrx driver provides that keeps you from having a functioning computer?

- rmjb

a laptop that has good graphic chip and stands without 3D acceleration is a really naked laptop and not stable in my eyes. I don't make make the move to Ubuntu if that isn't working. 
Some applications and games really want the 3D you see. Cedega for instance.

---

### Post by bunnny on 2006-07-25
Hi

This will be my first thread in this forum (thread in a BIG thread)

I have followed the guide exactly whith no errors, but when I reboot i just get a black screen, its active but just black.

I start to get realy bored about this, I have tried to find answears in this thread but no no.

I would be realy glad if someone could help me to get this working.

I have a x550 card and amd64 (running ubuntu 6.06 32-bit)

The log from GDM:

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux theone 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 25 17:23:56 2006
(==) Using config file: "/etc/X11/xorg.conf"
(WW) RADEON: No matching Device section for instance (BusID PCI:5:0:1) found
(**) RADEON(0): RADEONPreInit
(**) RADEON(0): RADEONScreenInit d8000000 0
(**) RADEON(0): Map: 0xd8000000, 0x08000000
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81ff800)
(**) RADEON(0): Read: 0x0030000c 0x00030065 0x00000000
(**) RADEON(0): Read: rd=12, fd=101, pd=3
(**) RADEON(0): RADEONSaveMode returns 0x81ff800
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x08000000
(**) RADEON(0):   agp_size         : 0x081ff6d8
(**) RADEON(0):   agp_base         : 0x081ff6d8
(**) RADEON(0):   MC_FB_LOCATION   : 0xdfffd800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1280x1024     157.50  1280 1344 1504 1728  1024 1025 1028 1072 (24,32) +H +V
1280x1024     157.50  1280 1344 1504 1728  1024 1025 1028 1072 (24,32) +H +V
(**) RADEON(0): Pitch = 10485920 bytes (virtualX = 1280, displayWidth = 1280)
(**) RADEON(0): dc=15750, of=31500, fd=140, pd=2
(**) RADEON(0): RADEONInit returns 0x82001b0
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x82001b0)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xdfffd800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x0001008c 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=12, fd=140, pd=1
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 203b7c7c
(**) RADEON(0): RADEONSaveScreen(0)
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(**) RADEON(0): Initializing backing store
(**) RADEON(0): DRI PCIGART param
(**) RADEON(0): DRI Finishing init !
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 160
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): Initializing DPMS
(**) RADEON(0): Initializing Cursor
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(**) RADEON(0): RADEONScreenInit finished
error opening security policy file /etc/X11/xserver/SecurityPolicy
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) RADEON(0): RADEONSaveScreen(2)
(**) RADEON(0): RADEONCloseScreen
(**) RADEON(0): RADEONDRIStop
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONDisplayPowerManagementSet(0,0x0)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff800)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0030000c 0x00030065 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=12, fd=101, pd=3
(**) RADEON(0): Disposing accel...
(**) RADEON(0): Disposing cusor info
(**) RADEON(0): Disposing DGA
(**) RADEON(0): Unmapping memory
(**) RADEON(0): RADEONDRICloseScreen

```

and the important stuff from my generated xorg.conf

```

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 96.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X600 (RV370)"
	Driver      "ati"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X600 (RV370)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
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

Excuse me for all text

Please help

---

### Post by Coty on 2006-07-26
Same problem, (first, sorry, i'm the first time around here) i get a black screen and everything halts ( i mean i can't even do ctrl+alt+f1 / f2 / ... )

what can i do?

---

### Post by Jaxilian on 2006-07-26
Someone interested in some serious troubleshooting with the problem I have with a Amilo D laptop and Radeon 9000 mobility chip?
All the howtos written so far in this forum has been useless and problem still remains. I get no 3D acceleration on it after I try the howtos and when I try "fglrxinfo" I get a lot of errors.

Please help!!. Prefer contact on MSN so we can solve this. I have 2 computers so I can chat on the other.

---

### Post by rmjb on 2006-07-26
> **Coty said:**
> Same problem, (first, sorry, i'm the first time around here) i get a black screen and everything halts ( i mean i can't even do ctrl+alt+f1 / f2 / ... )

what can i do?

I got this too, are you trying 64 bit on your ati based system? If so I'd recommend switching to 32 bit and bootsing with safe graphics mode. Then you can follow this HOWTO.

- rmjb

---

### Post by bunnny on 2006-07-26
I have got it to work now (after lot of tears and blood)

My problem was that my tv-out were connected, I just unpluggd it and it worked like a charm. THANKS

Now to get wine/cvscedega to work =P

---

### Post by trxDraxon on 2006-07-26
Thank you so much, worked perfectly on my Dell xps with a 9700!

---

### Post by Jaxilian on 2006-07-27
I got mine to work finally on Radeon 9000 mobility so I get good info when running the command fglrxinfo, but I can't get any data from glxgears. The cogwheels turns up, but no data comes out.
Any ideas?

---

### Post by Alyus on 2006-07-27
flodis

are you looking for the info from the 'glxinfo' command?

---

### Post by jamesrw on 2006-07-27
I'm still getting errors when running glxinfo and glxgears:
```
Error: couldn't get an RGB, Double-buffered visual

```

and another error running other apps like wine:
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  470
  Current serial number in output stream:  471

this is getting old.

---

### Post by rjz35 on 2006-07-28
Dear All,

As a total newbee on linux i did it again!!!!!!!!! thnx to you all for your information.
It's working now, ATI X300 on Dell latitude D610, fglrx 8.26.18 driver.
i will try to explain what i did [if i remember all].

Out of the box, fglrx did'nt work,then got it working by just install in the driver from the ati site. [the latest .run one] change the xorg.conf ati part to fglrx and it worked.

after playing around [as a newbee that is] installing al sorts of perfect software, thinks started to become slow,espacialy after recompiling the kernel [or how you al call it] when setting up MEDUSA4 [cad program, which is not working yet]. So i looked at fglrxinfo and saw mesa again.

OK, so let see, i started to instal the driver agian, no luck,
the best thing to do was to uninstall the driver from the terminal with.

sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo apt-get remove xorg-driver-fglrx 
edit xorg.conf in  device driver fglrx to Ati
then after reboot

sudo aptitude reinstall libgl1-mesa

install the ati driver

 ./ati-driver-installer-8.26.18-x86.run 

copy older version of libGL.so.1.2 [you'll find it on the forum] to usr/lib and usr/fglrx [make sure you are root].

edit xorg.conf again and reboot. 

among others i tried;
recompiling from scratch with the new ati driver;
install that other glx driver [don't remember the name, but i got stuck]

final word, don't stop rebooting, during this process of updating you need to reboot, don't ask me why.

hopes this help somebody, because it is a mess with that driver from ATI,

if i can help somebody pls let me know.

Robbert

---

### Post by TimJBart on 2006-07-28
> **rjz35 said:**
> 

install the ati driver

 ./ati-driver-installer-8.26.18-x86.run 

copy older version of libGL.so.1.2 [you'll find it on the forum] to usr/lib and usr/fglrx [make sure you are root].

edit xorg.conf again and reboot. 


I am a complete noob.  how do I move libGL.so.1.2 into those 2 folders.  they both say I do not have permissions.

I cannot get my video drivers to work after following the instructions.  It is struggling to spin the glxgears!

One question.  when I am configuring xorg, am I meant to be selecting ATI as the driver or something else?

---

### Post by rjz35 on 2006-07-28
> **TimJBart said:**
> I am a complete noob.  how do I move libGL.so.1.2 into those 2 folders.  they both say I do not have permissions.

I cannot get my video drivers to work after following the instructions.  It is struggling to spin the glxgears!

One question.  when I am configuring xorg, am I meant to be selecting ATI as the driver or something else?

Make sure that you get the root terminal running or go to synaptic package manager, install MC [midnignt commander], after that go to terminal launch midnight commander with: sudo mc. then go to the dir. and copy the files.

let me know if it works

---

### Post by rjz35 on 2006-07-28
> **TimJBart said:**
> I am a complete noob.  how do I move libGL.so.1.2 into those 2 folders.  they both say I do not have permissions.

I cannot get my video drivers to work after following the instructions.  It is struggling to spin the glxgears!

One question.  when I am configuring xorg, am I meant to be selecting ATI as the driver or something else?

> **rjz35 said:**
> Make sure that you get the root terminal running or go to synaptic package manager, install MC [midnignt commander], after that go to terminal launch midnight commander with: sudo mc. then go to the dir. and copy the files.

let me know if it works

after installing the mesa driver again you must in the driver section where states "fglrx" put "Ati"

---

### Post by TimJBart on 2006-07-28
what is the mesa driver, how do I change fglrc to Ati?

I replaced libGL.so.1.2 in usr/lib but I did not have a usr/fglrx folder.  Should I have?  I followed the directions in the 1st post of this thread exactly!

---

### Post by catlett on 2006-07-28
Thanks fizman49...*you the man!* It worked great. I always used the dapper guides method but it doesn't install the latest.
Thanks again.

---

### Post by d3viou5 on 2006-07-29
I just recently installed Ubuntu 6.06 and have been trying unsuccessfully to get 3D functionality out of my 9800 Pro.  I've tried several different methods posted here and other forums and so far the only one that's worked has been the one in this thread.  Thanks for posting this information!  It has helped me immensely!  Now I can finally try installing XGL!

---

### Post by MikeMLP on 2006-07-29
For those who may be wondering:  I was able to install the latest driver (8.27.10) using this method, just changing all instances of 8.26.18 to 8.27.10 in the instructions.
-Running ATI mobility 9600
-hf gl dd 0.o

---

### Post by ricesteam on 2006-07-29
I tried this method with the new 8.27.10 drivers but X-Server will not restart and I get this error:

X version mismatch, detected 7.1.1.0
required x.org 7.0-1.8


Any advice?

---

### Post by ricesteam on 2006-07-29
Hmm I got mine to work in a strange way.

I followed this guide many times, and I got fed up since everytime I reboot, the system would complain about xorg.conf not being 7.1.1 or 7.0 (unsure) so I just copied the xorg.conf.fglrx over to xorg.conf and reboot and PRESTO, my computer booted with correct ATI acceleration!

xorg.conf.fglrx is produce when you run
```
sudo aticonfig --overlay-type=Xv
```

Here's my fglrxinfo:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Generic
OpenGL version string: 2.0.5946 (8.27.10)

```

My current xorg.conf
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
#Section "Extensions"
#	Option	"Composite"  "Enable"
#EndSection

Section "ServerLayout"

#	Option		"AIGLX"	"true"
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
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
#	Load	"dbe"
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
	Identifier   "SyncMaster"
	HorizSync    50.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"

#	Option		"XAANoOffscreenPixmaps"
	Identifier  "ATI Technologies, Inc. R420 JK [Radeon X800]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. R420 JK [Radeon X800]"
	Monitor    "SyncMaster"
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


The only problem is my login screen: right after the Ubuntu splash screen, is the login screen which displays the wrong resolution. Its a very large resolution...but once I login everything is fine...

very strange.

---

### Post by bobby19 on 2006-07-29
What do you mean by Change to the download directory because I keep getting the no such file error.

---

### Post by ricesteam on 2006-07-29
I think I know how to fix the "MESA" problem...

You have to remove the xserver-xorg-driver-ati package, which in turns removes xserver-xorg-driver-all.  I just did a search of "fgl" in the Synaptic Package Manager and marked it for removal.

Not sure if is the true fix, but it worked for me. :)

---

### Post by Moldy Jello on 2006-07-30
i was wondering about the new drivers, the 8.27.10 ones, i installed them just fine on my desktop which uses an 1900xt but i dont want to mess up anything on my laptop, which is using the 8.25.16 i think, i forgot, but its something like that, and i forgot what method i used to get it done but they work, just curious if the new drivers will break my system i have the 200m in my laptop

---

### Post by MikeMLP on 2006-07-30
>  
What do you mean by Change to the download directory because I keep getting the no such file error. 

say you downloaded the driver package to your desktop.  In order to perform operations on it from the terminal, you have to let the terminal know your package is on the desktop.  to do that, I would do this (my home directory is "mike")

```
mike@Ubuntu:~$ cd /home/mike/Desktop
mike@Ubuntu:~/Desktop$

```

that is, I just type "cd /home/mike/Desktop" from the terminal where "cd" changes the directory to the directory that you type after "cd"

-Hope that makes sense

---

### Post by MikeMLP on 2006-07-30
@ moldy

There's only one way to find out.

if you need your laptop to be in perfect shape, and you don't have any specific reason for  attempting an upgrade, then don't attempt it.

I've been burned plenty of times by not heding the adage: "if it ain't broke, don't fix it."

---

### Post by jurgnn on 2006-07-31
Hello,

I have performance problems with 8.27.10 drivers, glxgears gives only 125fps, when it was over 1700fps with 8.25.x drivers.
Any idea what could cause this?

I must say that it doesn't feel very slow, tuxkart works well and blender is usable with 90k polys.

I installed driver with guide on first post of this thread.

Kernel: 2.6.15-26-k7

xx@xx:~$ fglrxinfo
> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.5946 (8.27.10)


xorg.conf:
> 
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fi"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mouse1"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Emulate3Buttons" "false"
	Option	    "Buttons" "7"
	Option	    "ZAxisMapping" "4 5"
	Option	    "ButtonMapping" "1 2 3 6 7"
	Option	    "Resolution" "100"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
#	Option      "PressCurve" "0,0,100,100" 		#Default
# 	Option      "PressCurve" "15,0,100,75"		#Firmer
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"          # Change to EVENT1
	Option	    "Type" "stylus"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
	Option	    "PressCurve" "5,0,60,100"		#Firmer
	Option	    "Speed" "0.8"			#Slower relative speed
EndSection

Section "Monitor"
	Identifier   "Q910"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver      "ati"
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
	Device     "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor    "Q910"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
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



xx@xx:~$ cat /var/log/Xorg.0.log | grep fglrx 
> 
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x81db778
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9550 (RV350 4153)" (Chipset = 0x4153)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x0200)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xdfef0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: IQT  Model: 2910  Serial#: 20021028
(II) fglrx(0): Year: 2002  Week: 44
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) fglrx(0): Gamma: 2.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing not preferred mode in violation of standard!(II) fglrx(0): redX: 0.638 redY: 0.325   greenX: 0.276 greenY: 0.596
(II) fglrx(0): blueX: 0.143 blueY: 0.066   whiteX: 0.283 whiteY: 0.297
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) fglrx(0): #5: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 55.0 MHz   Image Size:  360 x 270 mm
(II) fglrx(0): h_active: 640  h_sync: 672  h_sync_end 768 h_blank_end 864 h_border: 0
(II) fglrx(0): v_active: 480  v_sync: 488  v_sync_end 494 v_blanking: 530 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 110.0 MHz   Image Size:  360 x 270 mm
(II) fglrx(0): h_active: 1024  h_sync: 1056  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 812 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 150 Hz, H min: 30  H max: 110 kHz,
(II) fglrx(0): Monitor name: Q910
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Connected Display2: TV on TVDAC
(II) fglrx(0):  Display2: No EDID information from DDC.
(II) fglrx(0): Derived EDID from BIOS and internal tables for Display2:
(II) fglrx(0): Display2 EDID data ---------------------------
(II) fglrx(0): Manufacturer: PNP  Model: 9fe  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:
(II) fglrx(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing not preferred mode in violation of standard!(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): End of Display2 EDID data --------------------
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Secondary Controller - TV on TVDAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 250/196MHz @ 50Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 55 modes found for primary display.

Note: removed info about modes to save space

(==) fglrx(0): DPI set to (75, 75)
(==) fglrx(0): NoAccel = NO
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
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): cpuSpeedMHz: 0x00000706
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xd0954000 (size=0x076ac000)
(II) fglrx(0): UMM area:     0xd0954000 (size=0x076ac000)
[B](II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0[/B]
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7169000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.27.10
(II) fglrx(0):     Date: Jul 27 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.15-26-k7
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [agp] Mode=0x1f000a0b bridge: 0x1106/0x3189
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000b0a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xe0000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000302)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x00954000
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,1528)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1600 x 328
(**) fglrx(0): Video overlay enabled on CRTC1
(II) fglrx(0): Interrupt handler installed at IRQ 193.
(II) fglrx(0): Exposed events to the /proc interface


xx@xx:~$ dmesg | grep fglrx
> 
[17179607.508000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologie s, Starnberg, GERMANY' taints kernel.
[17179607.512000] [fglrx] Maximum main memory to use for locked dma buffers: 679  MBytes.
[17179607.512000] [fglrx] module loaded - fglrx 8.27.10 [Jul 27 2006] on minor 0
[17179613.372000] [fglrx] Internal AGP support requested, but kernel AGP support  active.
[17179613.372000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179613.372000] [fglrx] AGP detected, AgpState   = 0x1f000a0b (hardware caps o f chipset)
[17179613.464000] [fglrx] AGP enabled,  AgpCommand = 0x1f000302 (selected caps)
[17179613.476000] [fglrx] total      GART = 67108864
[17179613.476000] [fglrx] free       GART = 51113984
[17179613.476000] [fglrx] max single GART = 51113984
[17179613.480000] [fglrx] total      LFB  = 124436480
[17179613.480000] [fglrx] free       LFB  = 108974080
[17179613.480000] [fglrx] max single LFB  = 108974080
[17179613.480000] [fglrx] total      Inv  = 0
[17179613.480000] [fglrx] free       Inv  = 0
[17179613.480000] [fglrx] max single Inv  = 0
[17179613.480000] [fglrx] total      TIM  = 0


---

### Post by rippon on 2006-08-01
> **jurgnn said:**
> Hello,

I have performance problems with 8.27.10 drivers, glxgears gives only 125fps, when it was over 1700fps with 8.25.x drivers.
Any idea what could cause this?

I must say that it doesn't feel very slow, tuxkart works well and blender is usable with 90k polys.

I installed driver with guide on first post of this thread.

Kernel: 2.6.15-26-k7

xx@xx:~$ fglrxinfo


xorg.conf:



xx@xx:~$ cat /var/log/Xorg.0.log | grep fglrx 


xx@xx:~$ dmesg | grep fglrx

I am having a very similar issue. It says that 8.27.10 ATI driver is installed, but in glxgears I get around 140fps with my x800PRO AGP card. I can recall easily getting 8000+fps previously. Everything seemed to go without a hitch, but it just isn't performing like it should. Any solutions or ideas? Thanks.

---

### Post by whatever on 2006-08-01
> **rippon said:**
> I am having a very similar issue. It says that 8.27.10 ATI driver is installed, but in glxgears I get around 140fps with my x800PRO AGP card. I can recall easily getting 8000+fps previously. Everything seemed to go without a hitch, but it just isn't performing like it should. Any solutions or ideas? Thanks.
it's not a bug, it's a feature ;)
see this posting: [http://rage3d.com/board/showpost.php?p=1334478409&postcount=24](http://rage3d.com/board/showpost.php?p=1334478409&postcount=24)

---

### Post by franck.galbrun on 2006-08-01
Here everything went ok with a COMPAQ Presario v2000 / ATI RADEON XPress 200M and a clean Dapper install. Thanks.

---

### Post by kazbear on 2006-08-01
I have a Compaq Armada E500.  I think it has an ATI Mach 64.  I have tried many guides to get 3D acc going.  Nothing has worked so far.  I am also quite new to Linux/Ubuntu, so I don't fully understand the "whys" for each step.

Anyway, I tried the guide in this post.  Well written and I can follow along.  I did not get any errors along the way.  However, when I re-booted, X would not start.  Someone else in this thread had a similar issue and it was suggested to reconfigure xserver and choose the other driver.  I tried this and still it did not come back.  So I tried it again but choose the ati driver and X is now back.

But still, no 3d.

Any suggestions?

Thanks
kaz

---

### Post by catlett on 2006-08-01
Not to jump the thread especially when this guide has my card performing at it's best ever (As you can see, I broke 3000 for the first time. Not bad for a regular pci card with only 128mb :grin: )
```
catlett@ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
2366 frames in 5.0 seconds = 473.200 FPS
2989 frames in 5.0 seconds = 597.800 FPS
3069 frames in 5.0 seconds = 613.800 FPS
3083 frames in 5.0 seconds = 616.600 FPS
3057 frames in 5.0 seconds = 611.400 FPS
3072 frames in 5.0 seconds = 614.400 FPS
2941 frames in 5.0 seconds = 588.200 FPS
catlett@ubuntu:~$
```
Now to the jumping in the thread part. Have you tried the Dapper Guide procedure? It worked for me before I found the fitzman:D It doesn't have the latest driver. It is one update behind but if it works? Isn't a slightly older version better than no driver?
Anyways, here is the link [http://doc.gwos.org/index.php/DapperGuide#Installing_the_driver_.28ATI.29](http://doc.gwos.org/index.php/DapperGuide#Installing_the_driver_.28ATI.29)

---

### Post by kazbear on 2006-08-01
Thanks, I had not tried that one.  Same effect though.  X failed to start after reboot.

How do I get back to the original install of ubuntu?  I feel like all the things I am trying are just overlays of some driver I need to get rid of.  Perhaps something might work if I can install from a fresh setup?

---

### Post by catlett on 2006-08-02
Check your /etc/X11 directory and see if a backup was made during the installation. I have 2 different backups that I didn't make. I believe the 2 installations made a back up each when they changed my configuration.
Since you don't have gui, use cat to see if the file exits. (i.e. cat /X11 etc, use the tab completion feature to see what files are available. which means start typing a few letters and then hit the tab key. The terminal will then print out the file that has those letters at the start. My 2 files are /etc/X11/xorg.conf.fglrx-0 and the other one is 
/etc/X11/xorg.conf.original-0. If the file is there, use cp to change your list back. For example if I wanted to make the fglrx-0 version my regular xorg filew I would use this command
```
sudo cp /etc/X11/xorg.conf.fglrx-0 /etc/X11/xorg.conf
```

---

### Post by disciple on 2006-08-03
worked again for another reinstall, with 8.27.10


great work, again, on this howto

---

### Post by TimJBart on 2006-08-03
> **catlett said:**
> 
Now to the jumping in the thread part. Have you tried the Dapper Guide procedure? It worked for me before I found the fitzman:D It doesn't have the latest driver. It is one update behind but if it works? Isn't a slightly older version better than no driver?
Anyways, here is the link [http://doc.gwos.org/index.php/DapperGuide#Installing_the_driver_.28ATI.29](http://doc.gwos.org/index.php/DapperGuide#Installing_the_driver_.28ATI.29)

catlett - YOU ARE MY HERO!  IT WORKED

```
9892 frames in 5.0 seconds = 1978.293 FPS
9483 frames in 5.0 seconds = 1896.423 FPS
9882 frames in 5.0 seconds = 1976.286 FPS
9869 frames in 5.0 seconds = 1973.779 FPS
9884 frames in 5.0 seconds = 1976.727 FPS

```

Not sure why I hadn't already tried that, but now I'm not going to touch anything else just in case I break them!

Thanks

---

### Post by TimJBart on 2006-08-03
ok...I broke it.  Was running like a dream so I thought I'd install all the updates.  I did this, and now when ubuntu loads to desktop, it is in some strange tiny widescreen resolution that my screen cant display properly!

I didn't change anything but its gone wrong. Can I get it working in the correct resolution using:

```
sudo dpkg-reconfigure xserver-xorg
```

I have tried this but it doesn't seem to change anything.  Do I use ATI or gflrx driver?

---

### Post by Howcomes on 2006-08-03
Following the steps in the original post worked for me, no blacklisting required.

There was some deviance from those exact steps, but only what the Konsole told me to do. Something about not being able to build and to issue a apt-get -f install to resolve dependancy issues.

Other then that, these instructions worked just fine for me.
[It's a Radeon 9200 SE btw]

Oh yea! I modified the instructions to work with Breezy Badger as that is what im running, Where it says to run the package from ATi after chmod +x'ing it, i used --buildpkg Ubuntu/breezy instead of Ubuntu/dapper. So i guess i can confirm that these instructions and that package [latest one listed in original post] Work on 5.10 as well.

```

howcomes@the.world.has.turned.and.left.me.here:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.27.6)
howcomes@the.world.has.turned.and.left.me.here:~$ glxgears
5653 frames in 5.0 seconds = 1130.399 FPS
5617 frames in 5.0 seconds = 1123.385 FPS
5611 frames in 5.0 seconds = 1122.033 FPS
howcomes@the.world.has.turned.and.left.me.here:~$ uname -a
Linux the.world.has.turned.and.left.me.here 2.6.12-10-386 #1 Tue Jul 18 22:08:27 UTC 2006 i686 GNU/Linux

```

Thx
-Howcomes

---

### Post by catlett on 2006-08-03
> **TimJBart said:**
> ok...I broke it.  Was running like a dream so I thought I'd install all the updates.  I did this, and now when ubuntu loads to desktop, it is in some strange tiny widescreen resolution that my screen cant display properly!

I didn't change anything but its gone wrong. Can I get it working in the correct resolution using:

```
sudo dpkg-reconfigure xserver-xorg
```

I have tried this but it doesn't seem to change anything.  Do I use ATI or gflrx driver?

I would use vesa. It is basic driver that works with most hardware. It won't give you numbers like you posted though (BTW what kind of card are you running? I'm jealous. Those are the best numbers I ever saw!) But it should give you a graphical desktop.
Then run the procedure again.
WAIT A MINUTE. I think I know what happened. Did you get a new kernel with the update? If you did, that is it. If you don't remember, when you next boot select the second kernel. Not the recovery or memtest but the second in version  number. See if it boots then.
Actually now that I am thinking about it, if you ran sudo dpkg-reconfigure xserver-xorg then you can get the text login. Just run the commands from the text line. 
Do it like this. If you are at the text l;ogin, login. If you are in a crappy X and not the login, press ctrl+alt+F1 to get a console. Then run the driver install commands.
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) 
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```
Then reboot. If I had to guees it is because you have a new kernel. You will need to run this every time you get a new kernel.

---

### Post by M3phista on 2006-08-04
Has anyone got 3D acceleration to work under xgl-session?
Normal sessions work for me with the news fglrx from ATI.com, but
not when I login to XGL+Compiz-Sessions :-(

---

### Post by evilXhwnd on 2006-08-04
i got it to work too on my HP Pavilion zv6000, however, i had to go into the BIOS and disable sideport.

---

### Post by PiroS on 2006-08-05
I'm still having problems with my GIGABYTE RADEON 9250.I've tried several howto's but nothing helps.I'm getting only:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```
```
$ dmesg | grep fglrx
[17179590.708000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179590.712000] [fglrx] Maximum main memory to use for locked dma buffers: 430 MBytes.
[17179590.712000] [fglrx] module loaded - fglrx 8.27.10 [Jul 27 2006] on minor 0
[17179709.284000] [fglrx] Internal AGP is not supported in 2.6 kernel.
[17179709.284000] [fglrx:firegl_unlock] *ERROR* Process 4407 using kernel context 0

```
What should I do?

---

### Post by Dimitry Fayerman on 2006-08-05
> **EReckase said:**
> 
Everything looks until right at the end...the screen blanks as usual after when the boot process is nearly complete, but instead of a login screen, I get zilch, nada, just a black screen. 
I think I figured out the black screen problem, at least partially.
In my case it is associated with DVI output from the card. 
I have Dell 1905FP monitor connected to Radeon 9250 card. 
It looks like the DVI output does not work with fglrx driver. The screen goes to sleep not getting any signal. If I switch the monitor to connect to VGA plug, it works. 
DVI is working with open source driver.

I was playing with aticonfig trying to get the DVI to work but nothing seams to help.
I think it is treating DVI as a second monitor and it is not recognized.
I connected the second monitor to VGA and
tried
 sudo aticonfig --enable-monitor=ctrl1, crt2
and got:
ati_dm: FGLRX_EnableDisplays failed when try to enable display: 10.

The sudo aticonfig --query-monitor
gives:
  Connected monitors: crt1
  Enabled monitors: crt1
ATI support site has many reports about DVI not working in Windows with different monitors and cards. I suspect it is the same king of problem. I will report to ATI.

At least now I can get decent graphics performance even though display is not as crisp as with DVI.

---

### Post by tdwester on 2006-08-05
Just wanted to say thanks for the directions!!Worked great on my HP L2000.

---

### Post by rmjb on 2006-08-06
> **Dimitry Fayerman said:**
> I think I figured out the black screen problem, at least partially.
In my case it is associated with DVI output from the card. 
I have Dell 1905FP monitor connected to Radeon 9250 card. 
It looks like the DVI output does not work with fglrx driver. The screen goes to sleep not getting any signal. If I switch the monitor to connect to VGA plug, it works. 
DVI is working with open source driver.

I was playing with aticonfig trying to get the DVI to work but nothing seams to help.
I think it is treating DVI as a second monitor and it is not recognized.
I connected the second monitor to VGA and
tried
 sudo aticonfig --enable-monitor=ctrl1, crt2
and got:
ati_dm: FGLRX_EnableDisplays failed when try to enable display: 10.

The sudo aticonfig --query-monitor
gives:
  Connected monitors: crt1
  Enabled monitors: crt1
ATI support site has many reports about DVI not working in Windows with different monitors and cards. I suspect it is the same king of problem. I will report to ATI.

At least now I can get decent graphics performance even though display is not as crisp as with DVI.

I have DVI working on my X800.

- rmjb

---

### Post by kill_u on 2006-08-07
Hi 
I try this [howto]("http://www.ubuntuforums.org/showthread.php?t=24557") to install ATI drivers, and run correctly my ATI Radeon 9550. I play chromium and have not a problem with framerate.  The game runs normal. But my problem now is: How to run a TV-out, I use a different howto`s and wiki`s  without any effect. 
Anyone can help me? 

Sorry about my English

---

### Post by CBTF on 2006-08-07
> gsf@gsf-desktop:~$ chmod +x ati-driver-installer-8.27.10-x86.run
chmod: cannot access `ati-driver-installer-8.27.10-x86.run': No such file or directory


What now? The file is on my desktop..

---

### Post by kill_u on 2006-08-07
> gsf@gsf-desktop:~$ chmod +x ati-driver-installer-8.27.10-x86.run
chmod: cannot access `ati-driver-installer-8.27.10-x86.run': No such file or directory


try 
```

gsf@gsf-desktop:~$cd Desktop
gsf@gsf-desktop/Desktop:~$ chmod u+x ati-driver-installer-8.27.10-x86.run
gsf@gsf-desktop/Desktop:~$./ati-driver-installer-8.27.10-x86.run

```

or just type 
```
gsf@gsf-desktop/Desktop:~$sudo ./ati-driver-installer-8.27.10-x86.run
```

---

### Post by CBTF on 2006-08-07
> bash: gsf@gsf-desktop/Desktop:~: No such file or directory


is what that gives me.. i cant make sense of this.](*,)

---

### Post by chalex on 2006-08-07
> **CBTF said:**
> is what that gives me.. i cant make sense of this.](*,)

You should type only the stuff after the dollar sign.  The dollar sign is the prompt.

---

### Post by CBTF on 2006-08-07
thank you for pointing that out. i wasnt aware (winows n00b here ;))

**it now says i must be logged in as super user to run the installer.** what shall i do?
 
thanks to those patient enough to help me learn all this stuff.

---

### Post by PiroS on 2006-08-07
[QUOTE="CBTF"]thank you for pointing that out. i wasnt aware (winows n00b here )

it now says i must be logged in as super user to run the installer. what shall i do?

thanks to those patient enough to help me learn all this stuff.[/QUOTE]
$sudo chmod u+x ati-driver-installer-8.27.10-x86.run
(You will be prompted for your pass)
$sudo ./ati-driver-installer-8.27.10-x86.run

---

### Post by CBTF on 2006-08-07
edit: got it working. many thanks, extremely helpful community ;)

---

### Post by Cuppa-Chino on 2006-08-07
OK OK OK, please do not flame, knock me or anything I am probably going to be saying / asking stuff a million people have asked, **but**

there was a time when my lovely Radeon 9500 / 9700 worked I could run it at both 4 and 8 pixel pipes and all was lovely and cool and great and so on but now I just cannot get to work anymore

I have a suspicion that my xorg.conf file is the problem but I have no back up anymore
[U]
how can I reset the xorg.conf completely?[/U]

well here is the output and code:
mesa driver:
```
Cuppa-Chino@desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

xorg.conf - total below but I guess this might be the problem...
```
Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

](*,) pleeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeease help




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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbVariant" "nodeadkeys"
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
	Identifier   "S/T 71S"
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
	Device     "Generic Video Card"
	Monitor    "S/T 71S"
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

### Post by quad3d@work on 2006-08-09
[http://ubuntuforums.org/showpost.php?p=1188991&postcount=2](http://ubuntuforums.org/showpost.php?p=1188991&postcount=2)

**DISABLED_MODULES="fglrx"** in **/etc/default/linux-restricted-modules-common**

---

### Post by TFrog on 2006-08-10
ATI has released Version 8.27.10 of their 3D drivers for linux.  I ran the ATI method of installation.  With minimal input and two command line commands I'm now running the ATI drivers on my Compaq R4125US laptop.

First command:

sudo sh ./ati-driver-installer-8.27.10-x86.run

Then follow the graphical installer.  Unfortunately they didn't make it possible to generate deb files for installations.  They only do Redhat Enterprise Level 3 and 4 as well as Novell Suse all the way to the present level rpms.

Next you have to do:

sudo aticonfig --initial

And finally:

sudo aticonfig --resolution=0,1280x800

1280x800 is the resolution.  You can do multiple resolutions if you like.  I chose only the one i prefer to run.  Also, I ran tests with  glxgears -printfps and put all this into the screen shots below with screen shots of the actual ATI control panel.

---

### Post by TFrog on 2006-08-10
One last comment about the  glxgears -printfps tests in my prior posting.  The first was ran with the 200M chipset running Sideport 128 meg ram only (screenshot4.png).  The second test was run with Sideport and UMA for a total of 256 meg of ram (screenshot5.png).  The results are noticeably different but with the later you can still play some 3D games with this laptop with relative ease.  It's no hotrod but it's better than the 2D drivers when using Sideport only.

---

### Post by quad3d@work on 2006-08-11
.... I don't think you are using ATI drivers at all. Your first picture still shows Mesa under OpenGL.

My laptop is Compaq V2410US and have the X200M graphic card as well. My glxgears shows close to 900fps. See my attachment.

---

### Post by dgoran on 2006-08-12
ati 200 running 1500-1900 fps here. Ubuntu up to date running 8.25.18

-Goran

---

### Post by Cuppa-Chino on 2006-08-12
> **Cuppa-Chino said:**
> 
I have a suspicion that my xorg.conf file is the problem but I have no back up anymore
[U]
how can I reset the xorg.conf completely?[/U]

xorg.conf - total below but I guess this might be the problem...
```
Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

](*,) pleeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeease help



bump, any ideas how I can get it work - btw I have tried all manner of aticonfig's

---

### Post by TFrog on 2006-08-13
> **quad3d@work said:**
> .... I don't think you are using ATI drivers at all. Your first picture still shows Mesa under OpenGL.

My laptop is Compaq V2410US and have the X200M graphic card as well. My glxgears shows close to 900fps. See my attachment.

Yes I saw your attachment.  However I downloaded the latest drivers from ATI's site at:

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

I followed ATI's own instructions and came up with those readings running 32 bit Kubuntu on a Compaq 4125US.  What you were looking at was the open GL stuff in my attachments.  The driver used is the 8.27.10.  Now if I haven't gotten the open GL setup correctly, I'd appreciate some assistance.  Any improvement in the driver speed would be helpful as the 8.26.18 driver doesn't work for my laptop.  It booted to a blank screen after loading it.  Could be there are still steps I need to take.

---

### Post by TFrog on 2006-08-13
Ok.  I just tried the 8.27.10 drivers with the install instructions at:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually)

Following that persons instructions to the letter on a clean install of Kubuntu with all updates failed to load the 3D drivers (OpenGL) on my Compaq 4125US laptop](*,)   It didn't matter whether or not I had UMA+Sideport or if I had the video set in BIOS as only Sideport.  It went to bounced me back to the boot screen frozen.  I CAN get the 2D ATI driver working with ATI's install instructions but I'd love to see what I'm missing in overall speed by having the OpenGL loaded.  Alas, this is the third time I've tried this and I'm one who firmly believes in "three strikes and your out."  Till the get working fglrx drivers in the repositories again, I'll stick to the basic Mesa drivers as I don't have a real need for 3D acceleration.

Now if someone could come up with any ideas I'd be happy to listen and maybe even try them as I back up my important data and can reload Kubuntu without worries.

---

### Post by twstokes on 2006-08-14
On my Inspiron 6000 with an X300 I managed to successfully install 8.27.10. The only problem I found was when I went to reboot, shutdown, or log off the screen would just go black. To do anything I would have to hit either the power button or CTRL+ALT+DEL to shutdown or reboot.

I rolled back to 8.26.18 and I have no problems whatsoever. Has anyone else experienced this or seen a fix?

Thanks!

---

### Post by isharra on 2006-08-18
I could have sworn this worked 2 weeks ago. I am trying on a different machine (fresh install of  Ubuntu 6.06.1) I can't get the module-assistant download. I have base sources list with universe and multiverse enabled (though I'd have thought this should have been in main.) ](*,)

```
$ sudo apt-get install module-assistant build-essential 
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package module-assistant
```

---

### Post by Kobra on 2006-08-18
Ok, I followed the instructions for installing the ATI drivers, word for word, but when I reboot and look at my fglrxinfo, is still tells me that I'm running on Mesa.  Everything went ok, no faults or anything.  The cars I'm trying to install is a Radion 9600 SE.  PLEASE HELP!  I really want to play Quake and Warsow

---

### Post by Kjow on 2006-08-20
Hi all :)

I have Kubuntu 6.06 (fresh install) with laptop Acer Aspire 1682 WLMi (Radeon 9700 Mobility) and all it is ok with new 8.28.8 ATI Drivers (and this HowTo ;) ):

[[IMG]http://img153.imageshack.us/img153/4593/schermata102wo3.th.jpg[/IMG]](http://img153.imageshack.us/my.php?image=schermata102wo3.jpg)

Thank You and Bye :)

PS Ok... Now it's XGL time :mrgreen: ](*,)

---

### Post by Dropknee on 2006-08-20
All with this how-to is right, but when you are going to update your current drivers you become in a real headache with the 8.28.8, becuase simply wont install correctly, thats what happen to me, right now im searching for a solution, I have a open threat [here]("http://www.ubuntuforums.org/showthread.php?p=1401696#post1401696")  to try to get a solucion when you update your current drivers

---

### Post by Kjow on 2006-08-20
> **Dropknee said:**
> All with this how-to is right, but when you are going to update your current drivers you become in a real headache with the 8.28.8, becuase simply wont install correctly, thats what happen to me, right now im searching for a solution, I have a open threat [here]("http://www.ubuntuforums.org/showthread.php?p=1401696#post1401696")  to try to get a solucion when you update your current drivers

I hope it will more easy with next revision of drivers :p

PS NOW I have XGL working :D (but with a problem with login screen... there isn't. I must login with ALT+F1 and launch startx manually)

---

### Post by TooDamFast on 2006-08-20
> **whatever said:**
> it's not a bug, it's a feature ;)
see this posting: [http://rage3d.com/board/showpost.php?p=1334478409&postcount=24](http://rage3d.com/board/showpost.php?p=1334478409&postcount=24)

umm.. ive been working on this for about 8 hours becuase glxgears is retarded?  i went from a score of 9000 fps to 200.  I thought MY systems was broken.  maybe i should have tried a game to test before i reformatted... twice... al;dsjfl;kasdjf;lkja;lksdfj.....


amd 2700+
ati x850pro
1 gig of ram.

---

### Post by whatever on 2006-08-20
> **TooDamFast said:**
> twice...

:lol:

---

### Post by TFrog on 2006-08-20
Update on my attempts at getting the ATI drivers to work with my Compaq R4125US laptop.  I was able to get the repository drivers working but only with UMA set at 128meg.  I only saw a 500FPS increase in my glxgears report.  This kind of increase doesn't warrant the waste of the precious memory.  I'd much rather be able to run the SidePort memory instead of chewing up my slower system RAM for video.  Guess I'll wait to see if ATI will fix the issue.  It's doubtful even the latest drivers will work for me without the waste:(

---

### Post by TFrog on 2006-08-20
> **quad3d@work said:**
> .... I don't think you are using ATI drivers at all. Your first picture still shows Mesa under OpenGL.

My laptop is Compaq V2410US and have the X200M graphic card as well. My glxgears shows close to 900fps. See my attachment.

Can you tell me are you using UMA, UMA&SidePort, or

---

### Post by TFrog on 2006-08-20
> **quad3d@work said:**
> .... I don't think you are using ATI drivers at all. Your first picture still shows Mesa under OpenGL.

My laptop is Compaq V2410US and have the X200M graphic card as well. My glxgears shows close to 900fps. See my attachment.

Can you tell me are you using UMA, UMA&SidePort, or Sideport only?  I was able to get the 8.25.18 drivers from the repositories working with UMA only:(  From what all I've read the SidePort isn't working at all.  Nor is UMA&SidePort for a while now.

---

### Post by TooDamFast on 2006-08-20
this is a heads up.  i can get 40 fps in doom4 and 190 fps in glxgears.  the driver does NOT work with glxgears on some cards.  (get 210 fps in glxgears with the vesa driver :)  )  so dont have a heart attack if your gears score goes down the pipe.

---

### Post by Jolly Roger on 2006-08-23
So I followed the instructions of the wiki that is linked near the beginning of this thread that explains how to install the 8.28.8 drivers. Everything seems to have worked alright. There's one problem though. The output of fglrxinfo tells me I'm using the Mesa drivers. So am I really using the Mesa drivers or are the ATI drivers installed and the label is wrong?

---

### Post by kickblow on 2006-08-23
i am lost, really lost n00b. 

here's my xorg.conf: 
> 
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
	InputDevice    "Synaptics Touchpad"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID	"PCI:1:0:0"
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

 


my result of fglrxinfo:
> $ sudo fglrxinfo
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: unable to open display :0


result for glxinfo:
> $ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None

result from fglrx -display :1
> fglrxinfo -display :1 display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


this is from ati's most recent driver, 8.28.8. it was compiled and installed w/ kernel source (2.6.15-26-386).

i'm using a gateway cx200x tablet. it xgl/compiz  works supremely well before the recent ubuntu upsetting update.

xgl/compiz is the whole recent i jump into linux nerdwagin this week. but since the last update, i have spent several days w/O sleep trying to get back xgl. and i m tired and about to give up linux.

can some1 help me?

---

### Post by bourdagespl on 2006-08-23
> **TFrog said:**
> Can you tell me are you using UMA, UMA&SidePort, or Sideport only?  I was able to get the 8.25.18 drivers from the repositories working with UMA only:(  From what all I've read the SidePort isn't working at all.  Nor is UMA&SidePort for a while now.

I have a R4035ca and both ati and debian driver work with UMA only. We have to find how to use sideport memory.

---

### Post by Canute on 2006-08-23
> **TooDamFast said:**
> this is a heads up.  i can get 40 fps in doom4 and 190 fps in glxgears.  the driver does NOT work with glxgears on some cards.  (get 210 fps in glxgears with the vesa driver :)  )  so dont have a heart attack if your gears score goes down the pipe.

So then I guess this is normal:
```
canute@canute-desktop:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
1235 frames in 5.0 seconds = 246.998 FPS
1350 frames in 5.0 seconds = 269.707 FPS
1237 frames in 5.0 seconds = 247.248 FPS

canute@canute-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

canute@canute-desktop:~$ glxinfo | grep "direct rendering"
direct rendering: Yes
```

---

### Post by pcolamar on 2006-08-23
Ok, I followed all the steps but got my compiz/gnome screwed up.
the fglrxinfo tells :

Error: unable to open display :0

What did I do wrong ?

---

### Post by lozenge on 2006-08-24
This is really weird, I did the howto exactly, and everything worked out, no errors whatsoever, but I restarted and got this:

```
james@monkey:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

Any suggestions are greatly appreciated.

---

### Post by lozenge on 2006-08-24
Double post :(

---

### Post by compwiz18 on 2006-08-25
I wrote a script to for recreating the drivers when you reinstall Ubuntu.

I will take any ATI installer (ati-driver*.run) and will automatically create the debs, install them, and recompile the module for you.

Just make sure the your working directory is the same directory that the ATI installer is in.

By the way, this howto works with the 8.28.8 drivers on a 200M Express.

---

### Post by bourdagespl on 2006-08-25
> **compwiz18 said:**
> 

By the way, this howto works with the 8.28.8 drivers on a 200M Express.

does it works with the on-board memory enabled?

---

### Post by compwiz18 on 2006-08-25
I don't know, cause my 200M just eats part of my RAM.

---

### Post by RSL on 2006-08-26
Just a question: Does it matter that the debs being generated [and installed] are i386 when I'm running a 686 kernel? I've Googled and searched the forums but can't seem to find anything out. I hope it's okay because I can't figure out how to create 686 debs for it. Anyone?

Thanks.

---

### Post by compwiz18 on 2006-08-26
> **RSL said:**
> Just a question: Does it matter that the debs being generated [and installed] are i386 when I'm running a 686 kernel? I've Googled and searched the forums but can't seem to find anything out. I hope it's okay because I can't figure out how to create 686 debs for it. Anyone?

Thanks.
Same thing here, but they *do* provide graphics acceleration if you install them...which is weird, cause I'm running the k7 kernel and installing i386 packages...

---

### Post by Carbon Based on 2006-08-26
Ok, this is really frustrating me now. I'm trying to install the latest ATI drivers (8.28.8) on my Sony Vaio with a Mobility Radeon 9000. I've used the insructions from [here (method 2)]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually"). The install process itself goes smoothly, but when I restart, I get this error:

```
Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
       after 0 requests (0 known processed) with 0 events remaining.
```

This is my xorg.conf:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0   "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
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

Right now I'm running the exact same xorg.conf with "ati" replacing "fglrx" in the "Device" section, which works fine, but is still using Mesa. I've been working on this all day, someone please help!


EDIT: I did actually have one problem with the install. When the instructions tell you to edit /etc/default/linux-restricted-modules-common all I found there was a blank file. I just added the line "DISABLED_MODULES="fglrx"" to it and saved. Could this be a problem?

Also, I just tried "sudo dpkg-reconfigure xserver-xorg", selecting the fglrx driver, and got the same error. Now I'm thinking I may have to downgrade, (maybe method 1 from the wiki HOWTO?).

---

### Post by lozenge on 2006-08-27
```
james@monkey:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

No clue... I followed it word for word and this happens, hardware acceleration still failing. Any ideas?

---

### Post by hexxa on 2006-08-27
I have a hp pavilion zv6000
whit ati radeon 200m.
and no guide work :(

my fglrxinfo write out this:
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

and my xorg.conf
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
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
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

### Post by toasted on 2006-08-27
> **Carbon Based said:**
> Ok, this is really frustrating me now. I'm trying to install the latest ATI drivers (8.28.8) on my Sony Vaio with a Mobility Radeon 9000. I've used the insructions from [here (method 2)]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually"). The install process itself goes smoothly, but when I restart, I get this error:

```
Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
       after 0 requests (0 known processed) with 0 events remaining.
```

This is my xorg.conf:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0   "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
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

Right now I'm running the exact same xorg.conf with "ati" replacing "fglrx" in the "Device" section, which works fine, but is still using Mesa. I've been working on this all day, someone please help!


EDIT: I did actually have one problem with the install. When the instructions tell you to edit /etc/default/linux-restricted-modules-common all I found there was a blank file. I just added the line "DISABLED_MODULES="fglrx"" to it and saved. Could this be a problem?

Also, I just tried "sudo dpkg-reconfigure xserver-xorg", selecting the fglrx driver, and got the same error. Now I'm thinking I may have to downgrade, (maybe method 1 from the wiki HOWTO?).

You are not alone - check this out -
[http://www.ubuntuforums.org/showthread.php?t=239229](http://www.ubuntuforums.org/showthread.php?t=239229)

---

### Post by nixeri on 2006-08-27
Still the same thing with my laptop .. Mesa is all what i got.. I tested Ubuntu on my friends HP (different model, but has 200M too) and i got acceleration work. All what i needed to do was disable graphic chips own memory and use RAM instead. 

Unfortunately my laptop doesnt allow that  :( Im beginning to lose my faith..](*,) Back to Windows? NO!! .. Maybe i just hafta wait if AMD Decides to release ati drivers on open source.. :( Thanks for the Lord, acceleration works fine with my Desktop-PC (P4 3,2GHz, 1gig, ati x600 pro) .. XGL+Compiz also works..

---

### Post by toasted on 2006-08-27
you can always use older drivers till this gets fixed

---

### Post by kellingt on 2006-08-27
It is really helpful if you post any errors in the /var/log/Xorg.0.log file.  They can be found by searching for '(EE)'.

---

### Post by toasted on 2006-08-27
> **kellingt said:**
> It is really helpful if you post any errors in the /var/log/Xorg.0.log file.  They can be found by searching for '(EE)'.
I can do the install with no errors at all.. it just installs smoothly
No luck getting the mesa go go away though so I have gone back to earlier drivers that work. It looks to be a big problem eh?

Edit:
Actually there are some ee's in that file. Maybe I should start with a clean file and try the reinstall again? Wouldnt that give me only errors from that driver install and be accurate?

---

### Post by kellingt on 2006-08-27
It is really helpful if you post any errors in the /var/log/Xorg.0.log file.  They can be found by searching for '(EE)'.

---

### Post by kellingt on 2006-08-27
Sorry for the duplicate post...and for not being more specific.

Look at /var/log/Xorg.0.log after restarting X.  It will tell if any errors were detected while trying to start the xserver.

---

### Post by kickblow on 2006-08-27
hi xgl work for me now

fglxinfo gives this:
```
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 SE Generic
OpenGL version string: 1.2 (2.0.6011 (8.28.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

while fglrxinfo gives me this:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 SE Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

how do i fix this, so that jogl web start programs requiring extensions from gl work?

:(

---

### Post by maniacmusician on 2006-08-27
hey

i was wondering how i would go about completely removing the drivers that this howto installs. They have given me a lot of trouble in that I am unable to enable compositing, something i would really like to implement. I've tried it a bunch of times and no one seems to be able to help me out with it, so my next step is going to be trying to install the open source drivers and try enabling compositing with that. but first i need to completely remove these, so how would i do that?

PS. If anyone thinks they can help me get compositing working with these drivers, its not too late, i'd appreciate the help. previous threads i've started about this (explaining the problem): [http://ubuntuforums.org/showthread.php?t=236019](http://ubuntuforums.org/showthread.php?t=236019), [http://forum.xfce.org/index.php?topic=2703.0](http://forum.xfce.org/index.php?topic=2703.0)

---

### Post by Chopp on 2006-08-27
I've been trying now for some time to fix it on my computer using a Radeon 9200SE card..
But when I try to start X I get:
```
Fatal Server Error:
no screens found.
```
Same thing with fglrxinfo ..

This is the current xorg.conf file I use, been doing dpkg-reconfigure lost of times with diffrent values ^^
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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
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
	Identifier   "DELL P992"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Monitor    "DELL P992"
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
Xorg.0.log:
```
(EE) No devices detected.
```If you need any more info, just tell me .. I'm stuck :(

---

### Post by kickblow on 2006-08-28
> **maniacmusician said:**
> hey

i was wondering how i would go about completely removing the drivers that this howto installs. They have given me a lot of trouble in that I am unable to enable compositing, something i would really like to implement. I've tried it a bunch of times and no one seems to be able to help me out with it, so my next step is going to be trying to install the open source drivers and try enabling compositing with that. but first i need to completely remove these, so how would i do that?

PS. If anyone thinks they can help me get compositing working with these drivers, its not too late, i'd appreciate the help. previous threads i've started about this (explaining the problem): [http://ubuntuforums.org/showthread.php?t=236019](http://ubuntuforums.org/showthread.php?t=236019), [http://forum.xfce.org/index.php?topic=2703.0](http://forum.xfce.org/index.php?topic=2703.0)

there's a script from ati that uninstalls its fglrx driver from this instructions:
<a href="https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html">(un)install instructions</a>. that may help.

---

### Post by maniacmusician on 2006-08-28
thanks, i tried that. It said that it uninstalled fglrx, but fglrx still works for some reason lol. but i went ahead and tried the open source "ati" driver anyways.

my dilemna is, that when I use the "ati" driver, i have no hardware acceleration, and thus enabling Composite has no effect. When I use the proprietary fglrx driver, I can't enable the composite extension because when i do my desktop gets all screwed up. this sucks lol.

but thats a seperate issue, i'll start a thread about it. my question for the people using this thread is, can you guys successfully enable the Composite extension using this fglrx driver? 

thanks.

---

### Post by whatever on 2006-08-28
> **kickblow said:**
> 
how do i fix this, so that jogl web start programs requiring extensions from gl work?

:(
use plain Xorg instead of Xgl ;)

---

### Post by daniel_89 on 2006-08-28
Hi,
I have a Dell Dimension 8400 PC with x800SE graphic card.

I have installed the last fglrx driver to have 3d support
([Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually"))

When I restart my PC the graphic card gets hotter and hotter and after some minutes the graphic card stinks totally. :confused:  - I don't know what to do
any idea?
plz help

---

### Post by toasted on 2006-08-28
Is the fan running?

---

### Post by daniel_89 on 2006-08-28
Thankyou!!!
It's was a good idea (I was too silly to check this)
The fan ist really not working.

I don't know why because unter Windows the Graphic Card is workling without problems(the fan doesn't have to work unter Windows?!).
Maybe I can solve the problem now - I will post if I get a solution
daniel

---

### Post by toasted on 2006-08-28
Well you could always plug the fan into the power supply and run it full time... at least I think you should be able to. Check to make sure the voltages are the same first.

---

### Post by Chopp on 2006-08-28
Ok. I've been doing some changes for my 9200SE card and I find this xorg.conf to be correct, but it I still get the error **no screens found**.
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
	Identifier   "DELL P992"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID	"PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Monitor    "DELL P992"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier		"Default Layout"
	Screen		"aticonfig-Screen[0]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     	"stylus" "SendCoreEvents"
	InputDevice     	"cursor" "SendCoreEvents"
	InputDevice     	"eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode         0666
EndSection

```
[QUOTE=X.org wiki]**(EE) No devices detected.**

It is very likely that your xorg.conf file doesn't contain the correct driver(s) for the chipset(s) in your system or that your chipset isn't supported by any of the drivers. [/QUOTE]

---

### Post by yyagol on 2006-08-29
[SIZE="6"]Than you so much for this How-To,
it realy works for me from a fresh install, and its
the first how to that dose that.
again thanks:-D [/SIZE]

---

### Post by daniel_89 on 2006-08-29
@toasted
I have found the problem.
The fan is defect.
I will buy a new one what will solve the problem I think.
thx for helping
daniel

---

### Post by kellingt on 2006-08-29
> Ok. I've been doing some changes for my 9200SE card and I find this xorg.conf to be correct, but it I still get the error no screens found.

Hey Chop...your first xorg.conf file didn't have a modes setting for the specified screen...this one doesn't have a "Viewport".  It doesn't really matter, but for completeness....

[INDENT]Section "Screen"
	[INDENT]Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
	[INDENT][COLOR="Cyan"]	Viewport   0 0[/COLOR]
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"[/INDENT]
	EndSubSection[/INDENT]
EndSection[/INDENT]

Can you post your Xorg.0.log from when you try to run with the fglrx drivers?  It should be copied to /var/log/Xorg.0.log.old when you reboot into whatever X session that works.

---

### Post by Chopp on 2006-08-29
@kellingt
Thanks for your reply, I added the Viewport, but the problem consists.

Here's my Xorg.0.log :
```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux emil-desktop 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 29 16:48:25 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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

(II) PCI: Found 0 domains.
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3189 card 1043,807f rev 80 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,810d rev 60 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80ed rev 78 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xf7ffffff (0x18000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[1] -1	0	0xde800000 - 0xde8000ff (0x100) MX[B]
	[2] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[3] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[4] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[5] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[6] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[7] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[8] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[9] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[1] -1	0	0xde800000 - 0xde8000ff (0x100) MX[B]
	[2] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[3] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[4] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[5] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[6] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[7] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[8] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[9] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[5] -1	0	0xde800000 - 0xde8000ff (0x100) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[9] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[11] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[12] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[13] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[14] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[15] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
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
	compiled for 6.8.99.8, module version = 8.26.18
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
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9250/9200 Series (RV280 5961),
	RADEON 9250/9200 Series (RV280 5962),
	RADEON 9250/9200 Series (RV280 5964), FireMV 2200 PCI (RV280 5965),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300/X550 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 SE (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600/X550 Series (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 GTO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), FireGL V7200 (R480 5D50),
	RADEON X850 XT (R480 5D52), RADEON X850 (R481 4B48),
	RADEON X850 XT (R481 4B49), RADEON X850 SE (R481 4B4A),
	RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), RADEON X700 XT (RV410 5E4A),
	RADEON X700 PRO (RV410 5E4B), RADEON X700 SE (RV410 5E4C),
	RADEON X700 (RV410 5E4D), RADEON X700/X550 Series (RV410 5E4F),
	MOBILITY RADEON X700 (M26 5652), MOBILITY RADEON X700 (M26 5653),
	MOBILITY RADEON X700 XL (M26-XC 564F),
	RADEON 9000/9100 IGP Series (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000 IGP (RL300MB 7835),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 XT (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 Series (R520 7108),
	RADEON X1800 Series (R520 7109), RADEON X1800 Series (R520 710A),
	RADEON X1800 Series (R520 710B), RADEON X1800 Series (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	RADEON X1300 PRO (RV505 7143), RADEON X1300 (RV505 7147),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1300 Series (RV505 715F), RADEON X1600 Series (RV515 7140),
	RADEON X1300 Series (RV515 7142), MOBILITY FireGL (M54 GL 7144),
	MOBILITY RADEON X1400 (M54 7145), RADEON X1300 Series (RV515 7146),
	MOBILITY RADEON X1300 (M52 7149), MOBILITY RADEON X1300 (M52 714A),
	RADEON X1300 Series (RV515 714D), RADEON X1300 Series (RV515 714E),
	FireGL V3300 (RV515 7152), RADEON X1300 Series (RV515 715E),
	RADEON X1300 (RV516 7180), RADEON X1300 (RV516 7183),
	MOBILITY RADEON X1450 (M64P 7186), RADEON X1300 (RV516 7187),
	MOBILITY RADEON X1350 (M62P 718B),
	MOBILITY RADEON X1350 (M62CSP64 718C),
	MOBILITY RADEON X1450 (M62CSP128 718D),
	MOBILITY RADEON X1350 (M62S 7196), RADEON X1900 (R580 7240),
	RADEON X1900 (R580 7243), RADEON X1900 (R580 7244),
	RADEON X1900 (R580 7245), RADEON X1900 (R580 7246),
	RADEON X1900 (R580 7247), RADEON X1900 (R580 7248),
	RADEON X1900 (R580 7249), RADEON X1900 (R580 724A),
	RADEON X1900 (R580 724B), RADEON X1900 (R580 724C),
	RADEON X1900 (R580 724D), RADEON X1900 (R580 724E),
	RADEON X1900 (R580 724F), RADEON X1600 Series (RV530 71C0),
	RADEON X1600 Series (RV530 71C2), MOBILITY FireGL V5200 (M56 71C4),
	MOBILITY RADEON X1600 (M56 71C5),
	RADEON X1600 Series (RV530 LE 71C6),
	RADEON X1600 Series (RV530 VE 71CE), FireGL V3400 (RV530 71D2),
	FireGL V5200 (RV530 71DA), RADEON X1600 Series (RV530 SE 71DE)
(II) ATI Proprietary Linux Driver Version Identifier:8.26.18
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.26g1                           
(II) ATI Proprietary Linux Driver Build Date: Jun 22 2006 12:50:04
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.26.1-driver-lnx-275228
(EE) No devices detected.

Fatal server error:
no screens found
```

Edit:
Btw, I can't get my X to work with any drivers anymore ](*,)

---

### Post by kellingt on 2006-08-29
Chopp...your xorg.conf file worked in my system.  I wonder if your busid is incorrect?  Do an lspci and look for your vga controler.  The busid is the first column.

Mine looks like this:

[INDENT]0000:01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)[/INDENT]

So, my bus ID in my xorg.conf is:

Section "Device"
	[INDENT]Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID	"PCI:1:0:0"
[/INDENT]EndSection

---

### Post by Chopp on 2006-08-29
@kellingt
Thanks once again.
I've checked my lspci and I get this output:
0000:01:00.0 VGA compitable controller: ATI Technologies Inc RV280 [Radeon 9200SE] (rev 01)
0000:01:00.1 VGA Display controller: ATI Technologies Inc RV280 [Radeon 9200SE] (Secondary) (rev 01)

I've tested using PCI:1:0:1 , but I'm pretty sure thats my DVI output, and I currently use a VGA screen

---

### Post by kellingt on 2006-08-29
> **Chopp said:**
> 
Thanks once again.
I've checked my lspci and I get this output:
0000:01:00.0 VGA compitable controller: ATI Technologies Inc RV280 [Radeon 9200SE] (rev 01)
0000:01:00.1 VGA Display controller: ATI Technologies Inc RV280 [Radeon 9200SE] (Secondary) (rev 01)

I've tested using PCI:1:0:1 , but I'm pretty sure thats my DVI output, and I currently use a VGA screen

It looks like the PCI Scan that takes place when X is starting up didn't find your Display controller

Here is what my PCI Scan looks like:

[INDENT](II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3340 card 1014,0529 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,3341 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1014,052d rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1014,052d rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1014,052d rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1014,052e rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1014,052d rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1014,052d rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1014,0537 rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1014,055a rev 01 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e54 card 1014,054f rev 80 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 104c,ac46 card 4000,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 02:00:1: chip 104c,ac46 card 4800,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 02:01:0: chip 8086,101e card 1014,0549 rev 03 class 02,00,00 hdr 00
(II) PCI: 02:02:0: chip 168c,1014 card 17ab,8331 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan[/INDENT]

You can see that there is a match for my lspci that I posted earlier....and I don't see a match for your scan.

I'm sorry, but I don't really know how to fix that???  Perhaps you can check your bios to see if there is some sort of conflict???

Wish I could help more.

---

### Post by lH)4~mK0e on 2006-08-30
One thing that is very important, make sure you get the driver that fits your classification (i.e. Motherboard, Notebook, etc.) they are different filesizes.  I downloaded the wrong one today and my libGL did not work.

---

### Post by Chopp on 2006-08-31
I got it to work now.
The problem was that I were using X 10.3. When I updated to 10.4 I got it working again :D (Damn, I'm happy now9

---

### Post by MalReynolds on 2006-08-31
I'm pretty much a newb at this.  I've been trying to get this working on my Compaq v5101 with the Radeon 200m.

I'm actually running Kubuntu.  I've been able to get everything else working, ie. Automatix, Broadcom 4318 wireless.

When I try to install the latest driver, 8.28.18, I have trouble when I get to:

Create .deb packages:

Code:
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper


I'm assuming the Ubuntu/Dapper needs to be changed.  I tried Kubuntu/Dapper but that failed.

Any thoughts?

Thanks,
Scott

---

### Post by kellingt on 2006-09-01
> **MalReynolds said:**
> 
Code:
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper


I'm assuming the Ubuntu/Dapper needs to be changed.  I tried Kubuntu/Dapper but that failed.

Any thoughts?

Thanks,
Scott

Did you try it with Ubuntu/dapper?  The only big difference between Ubuntu and Kubuntu is the window manager, and that shouldn't effect the xserver.

---

### Post by toasted on 2006-09-01
> **MalReynolds said:**
> I'm pretty much a newb at this.  I've been trying to get this working on my Compaq v5101 with the Radeon 200m.

I'm actually running Kubuntu.  I've been able to get everything else working, ie. Automatix, Broadcom 4318 wireless.

When I try to install the latest driver, 8.28.18, I have trouble when I get to:

Create .deb packages:

Code:
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper


I'm assuming the Ubuntu/Dapper needs to be changed.  I tried Kubuntu/Dapper but that failed.

Any thoughts?

Thanks,
Scott

You have to change the name of the driver to the one you are using... all through the how to this is required if you are using different drivers than they are. 

Example
```
chmod +x ati-driver-installer-8.28.18-x86.run
./ati-driver-installer-8.28.18-x86.run --buildpkg Kubuntu/dapper
```

---

### Post by neo_reloaded on 2006-09-01
Oh my god oh my god oh my god ](*,) 
this is driving me mad.

All I do was to upgrade my kernel and restricted modules
kernel is -2.6.15-26-686
and I CANNOT GET FGLRX WORKING!!!

I AM GOING TO UNINSTALL UBUNTU AND re-instlal M$ WINDOWS..

This is the 100th time I am bitten by video issues on Linux !
can anybody help before I go mad?
Please look up
[http://ubuntuforums.org/showthread.php?t=247694](http://ubuntuforums.org/showthread.php?t=247694)

---

### Post by toasted on 2006-09-01
New kernel.. did you compile?

If not then do this:
```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```

---

### Post by neo_reloaded on 2006-09-01
There is nothing left to do..
every other how to, every other forum tried out!
](*,)

---

### Post by toasted on 2006-09-01
Well, you said
> All I do was to upgrade my kernel and restricted modules
kernel is -2.6.15-26-686

You have to compile after a kernel upgrade thats why I suggested it

---

### Post by neo_reloaded on 2006-09-01
Oh I am sorry, I agree ... that message was a bit misleading.
I did get latest ati binary driver and followed compile/install steps.
I am afraid this is going to spoil my long weekend..
I am already searching for my win XP CD.. :-({|=

---

### Post by compwiz18 on 2006-09-01
Before you do that, give [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910) a shot.  It's easy, and it doesn't take very long.

---

### Post by neo_reloaded on 2006-09-01
Guys! thanks for the community support.  but I did this a gazillion times ... I dont know how many times I typed
sudo reboot -n 
since last Monday :frown: 

The forum post is a copy of [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually")
if I am not mistaken
](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by toasted on 2006-09-01
Yea but fitzman49 uses the older ATI driver. Its all I can use for some reason. I cant seem to use the newer drivers so maybe it would help you too....

Edit... 
oops you are using an even older driver...
Well, dont give up

---

### Post by compwiz18 on 2006-09-01
The howto I posted is different then the link that you provided.  Try it?

---

### Post by compwiz18 on 2006-09-01
The you can use the newest driver ATI has for [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910) and it works fine.  At least for me.

---

### Post by neo_reloaded on 2006-09-01
Thanks fellas
hey compwiz what card do you have?

I am on a thinkpad t42p with FireGL mobility t2

---

### Post by compwiz18 on 2006-09-01
> **neo_reloaded said:**
> Thanks fellas
hey compwiz what card do you have?

I am on a thinkpad t42p with FireGL mobility t2
I've got a 200M...

I hope you can get that to work.

---

### Post by OmniDistortion on 2006-09-02
I did as the directions said and it keeps defaulting to Mesa I think. MistaED was helping me in the IRC channel yet we could not resolve it. Under xorg.0.log I get this error and it's the closest thing we've found to be the source of the problem:

"(WW) fglrx(0): "DRI initialization failed! (maybe driver kernal module missing or bad) 2D acceleration available MMIO no 3D acceleration available"

It's a 200m in a Toshiba A105-S1712 laptop.

---

### Post by Cuppa-Chino on 2006-09-02
Hi have also trawled the Xorg.0.log 

the core problems is:
```
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.28.8
(II) fglrx(0):     Date: Aug 17 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.15-26-686
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7f71000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

I am not sure how to fix this one?

It looks like it found my card okay in the code:
```

(II) PCI: PCI scan (all values are in hex)
... abbreviated
(II) PCI: 01:00:0: chip 1002,4144 card 148c,2057 rev 00 class 03,00,00 hdr 80 **this is my Radeon 9500 chipID**
(II) PCI: 01:00:1: chip 1002,4164 card 148c,2056 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
... abbreviated
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.28.8
	ABI class: X.Org Server Extension, version 0.2
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
```


(a partially abbreviated version attached)

---

### Post by krajok on 2006-09-03
Not work for me, I still got.

**** INVALID IO ALLOCTION ****

---

### Post by Furman on 2006-09-05
After Step:
sudo module-assistant prepare,update

i get:
Getting source for kernel version: 2.6.15-26-386
apt-get install linux-headers-2.6.15-26-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.15-26-386


Anyone know how to fix this?

Edit: ive tried apt-get to install the headers and it says that those heads dont exist the latest version is 2.6.13 i belive is there away i can use these if so how?

---

### Post by neo_reloaded on 2006-09-05
I gave up dabbling with new drivers.
May be it has to do with the driver. ](*,) 

I installed version 8.25.18 and things are working fine.
glxgears posts very decent FPS
direct rendering - yes

Kernel - 2.6.15-26-686 
Video card - ATI MOBILITY FIREGL T2
Driver version - 8.25.18

everything works ? = YES
:rolleyes: happy for the time being

---

### Post by lozenge on 2006-09-06
I get errors:

```

 &#9474; dh_testroot
 &#9474; rm -f configure-stamp                                                      &#9618;
 &#9474; rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a                               &#9618;
 &#9474; rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd                        &#9618;
 &#9474; rm -rf .tmp_versions                                                       &#9618;
 &#9474; rm -rf patch                                                               &#9618;
 &#9474; dh_clean                                                                   &#9618;
 &#9474; rm /usr/src/modules/fglrx/debian/control                                   &#9618;
 &#9474; rm /usr/src/modules/fglrx/debian/dirs                                      &#9618;
 &#9474; if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \           &#9618;
 &#9474;         cat /usr/src/modules/fglrx/debian/control.template >               &#9618;
 &#9474; /usr/src/modules/fglrx/debian/control; \                                   &#9618;
 &#9474;         fi                                                                 &#9618;
 &#9474; if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \                   &#9618;
 &#9474;         mv /usr/src/modules/fglrx/debian/postinst 
/usr/src/modules/fglrx/debian/fglrx-kernel-2.6.17.11.postinst; \           &#9618;
 &#9474;         fi                                                                 &#9618;
 &#9474; dh_testdir                                                                 &#9618;
 &#9474; touch configure-stamp                                                      &#9618;
 &#9474; dh_testdir                                                                 &#9618;
 &#9474; /usr/bin/make -C /usr/src/kernel-headers-2.6.17.11                         &#9618;
 &#9474; SUBDIRS=/usr/src/modules/fglrx modules                                     &#9618;
 &#9474; make[1]: Entering directory `/usr/src/kernel-headers-2.6.17.11'            &#9618;
 &#9474; /usr/src/kernel-headers-2.6.17.11/arch/i386/Makefile:38:                   &#9618;
 &#9474; /usr/src/kernel-headers-2.6.17.11/arch/i386/Makefile.cpu: No such file     &#9618;
 &#9474; or directory                                                               &#9618;
 &#9474; make[1]: *** No rule to make target                                        &#9618;
 &#9474; `/usr/src/kernel-headers-2.6.17.11/arch/i386/Makefile.cpu'.  Stop.         &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.11'             &#9618;
 &#9474; make: *** [build] Error 2
```

---

### Post by Cuppa-Chino on 2006-09-08
hi, after some help from here : [http://www.ubuntuforums.org/showthread.php?t=190341]("http://www.ubuntuforums.org/showthread.php?t=190341")
I manged to get rid of this error:
```
[B](EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP[/B]
```
essentially needed to correct an error in the kernel description of my chipset

**BUT** fglrx still not accelerating 3d Mode

```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc8000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
```

new Xorg.conf attached, any ideas...

---

### Post by daller on 2006-09-09
Do you have any experience with this guide, - on edgy?

I'm having a hard time with my ATI-card(s)

---

### Post by Mazza558 on 2006-09-10
> **Cuppa-Chino said:**
> hi, after some help from here : [http://www.ubuntuforums.org/showthread.php?t=190341]("http://www.ubuntuforums.org/showthread.php?t=190341")
I manged to get rid of this error:
```
[B](EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP[/B]
```
essentially needed to correct an error in the kernel description of my chipset

**BUT** fglrx still not accelerating 3d Mode

```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc8000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
```

new Xorg.conf attached, any ideas...

Hmm, that's exactly what I get, it says the device is -1... and then it says it's failed. 

This is what it says further up in the xorg log: 

```
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
```

and then further down:
```

(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

---

### Post by FyreBrand on 2006-09-14
I have the 8.28.8-1 drivers installed.  Thank you fitzman49 for a thorough HowTo.

I understand the part about recompiling when there is a new kernel or a kernel version update.  I do have two questions that I'm not sure on in the procedure.

1. When an new ATI driver is released can I use the procedure to install over the old driver or do I have to remove the old driver first?

2. When I recompile on a kernel update I'm assuming that is the only step I need to take and that I don't have update my xorg.conf file.  Is that true?  I would think the only time I might need to update the xorg.conf file is if I returned to using the mesa driver or when I update the ATI driver.

Again, many thanks fitzman49!

---

### Post by Freestyle Skater on 2006-09-14
I installed everything following the instructions for the 64-bit processors, and I get the following results:

> 
x@x:~$ fglrxinfo
Error: couldn't find RGB GLX visual!

x@x:~$ glxgears
Error: couldn't get an RGB, Double-buffered visua


I'm running a 64-bit Presario with a Radeon Express 200m.  I have a fairly fresh install of Ubuntu Dapper Drake 6.06 for 64-bit processors.  Here's my xorg.conf file  

> 
#opening

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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

*input stuff cut out*

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x768"
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



3-D acceleration isn't a deal breaker for me on Linux, but I'd appreciate any help.

---

### Post by snteran on 2006-09-14
I'm trying to update my ati driver because my screen resolution only offers 800 x 600.  I have installed the driver, now I am at the compile section and I am not able to proceed.
Any advice?  
user@Computer1:~$ sudo module-assistant prepare,update
sudo: module-assistant: command not found
user@Computer1:~$ sudo module-assistant prepare,update
sudo: module-assistant: command not found
user@Computer1:~$
Thanks

---

### Post by jngtt on 2006-09-14
i got the same problem as freestyle skater, i followed the method posted on the wiki

---

### Post by snteran on 2006-09-16
> i followed the method posted on the wiki

I'm sorry, but I'm not sure what you mean by the wiki post.  I looked through the posts again and not sure what you mean.  I feel like I'm almost done with the install of the driver, I guess I just need to compile.  I'm thinking that I might just need to be in the right directory for the update command to work.  I did a search for module-assistant but I'm not sure it is something I can search for.  I can't believe how difficult it is to update a driver.  I'm in for a long road with learning Linux. :)

---

### Post by arcane411 on 2006-09-16
fglrxinfo shows:
  display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

 i checked the xorg logs they show fglrx driver load failed here is the log
 i am using ati x1400 in my laptop.

  ESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M54P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"

---

### Post by nightmareci on 2006-09-16
fitzman49, I have to say this:
YOU ARE MY SAVIOR!!!
I have wanted to get hardware acceleration to work in Linux for many, many months, and have neglected using Linux until now (because Windows crapped out on me, so I was forced to...), but after following your instructions, my ATI Radeon 9800 XT works perfectly in Linux, no Mesa for me! I will now commence using Linux almost exclusively, because getting the drivers to work was one of the bigger steps I needed to make to ditch Windows. Now, to just learn that darned commandline better... :D

---

### Post by snteran on 2006-09-17
How do yo edit the source.list file, when I open the file, I'm only able to open it as read-only.  I am unable to remove the '#' from the unverise and mulit to be able to compile the driver?

Thanks,

---

### Post by arcane411 on 2006-09-17
open as superuser.. 
code
sudo gedit source.list

---

### Post by FyreBrand on 2006-09-17
> **snteran said:**
> How do yo edit the source.list file, when I open the file, I'm only able to open it as read-only.  I am unable to remove the '#' from the unverise and mulit to be able to compile the driver?

Thanks,I would recommend this thread on enabling repositories in your sources list.  [Ubuntu-Demon's source.list]("http://www.ubuntuforums.org/showthread.php?t=185758")

There are also a couple other good threads in that forum.  It is the repository forum.  Ubuntu-Demon and some others have posted some really good information with a few HowTo's on making things work.  I would recommend reading through the stickies in that forum and then coming back here and going through fitzman49's procedure.  That way you will have the proper repositories enabled and the rest of your packages up to date.

---

### Post by gfd on 2006-09-17
It worked like a charm... thank you!

---

### Post by TrinitronX on 2006-09-21
Today after the new kernel update to version 2.6.15-27-686, I went through the steps to re-install fglrx version 8.28.8 as I always have done with kernel updates... however, fglrxinfo keeps reporting Mesa:
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

So, I went back, uninstalled the packages in order, attempted to modprobe -r the fglrx module, but it said it was in use, even though my machine was running Mesa.  I could also tell because of the horribly slow OpenGL performance I was getting.

I then rebooted, booting to the recovery console so that Xorg wouldn't even load, and therefore fglrx would not be loaded.  Then I removed the kernel modules.  Next, I repeated the process, running the ati .run to make the .deb packages, re-installed them, went into the /usr/src/linux-headers-2.6.15-27-686 folder and ran a 'sudo make oldconfig' to make sure that the module would definately compile with the correct config.  Again, I built and installed the kernel module with module-assistant, then ran 'depmod' and 'modprobe -i fglrx'.  Rebooted, and again fglrxinfo gives the same output... stuck with Mesa :(

I then just ran the .run file normally, using the GUI to re-install the drivers, ran fglrxinfo: MESA :(.  I've made sure I have all the correct dependencies and the right version of gcc, checked my Xorg.0.log file for errors, and nothing really seems wrong, aside from some strange 'drmOpenDevice: open result is -1, (No such device)' errors that I've seen before since some version of the driver that I can't remember.  However, never has the driver not worked since then until now.
I'm stumped... what am I forgetting?

I've got a  Radeon 9800pro 128Mb card.  My Xorg.0.log is attached, and what's weird is that it shows the driver loading, and DRI loading as well.  According to the log, everything should be fine... but why does it not like the new kernel?

---

### Post by TrinitronX on 2006-09-22
I just attempted to install the 8.29.6 drivers today using the usual method, still not working.

However, after looking into some more error messages, I may know what the problem is.

When running `dmesg | grep fglrx`, I get:
```
dmesg | grep fglrx
[17179591.804000] [fglrx] Maximum main memory to use for locked dma buffers: 1412 MBytes.
[17179591.804000] [fglrx] module loaded - fglrx 8.29.6 [Sep 19 2006] on minor 0
[17179608.780000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179608.780000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179608.780000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[17179608.784000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179608.792000] [fglrx] total      GART = 268435456
[17179608.792000] [fglrx] free       GART = 252440576
[17179608.792000] [fglrx] max single GART = 252440576
[17179608.792000] [fglrx] total      LFB  = 126791680
[17179608.792000] [fglrx] free       LFB  = 116002816
[17179608.792000] [fglrx] max single LFB  = 116002816
[17179608.796000] [fglrx] total      Inv  = 0
[17179608.796000] [fglrx] free       Inv  = 0
[17179608.796000] [fglrx] max single Inv  = 0
[17179608.796000] [fglrx] total      TIM  = 0

```

Hmm... so the new kernel has AGP support compiled into it?  That theoretically shouldn't cause too much of a problem, but ATI of course recommends their internal AGP support instead.

Also, something quite interesting arose when running glxinfo with verbose debug messages:
```
LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 8.29.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
[COLOR="Red"]libGL error: dlopen /usr/lib/dri/fglrx_dri.so failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __glXFindDRIScreen)
libGL error: unable to load driver: fglrx_dri.so[/COLOR]
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier, 
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

```

So... apparently fglrx's dri support is messed up somehow, so instead it's using Mesa.  What's with the "undefined symbol: __glXFindDRIScreen" though?  Any way to fix this, or is it compiled in?

EDIT: After further research, I found that supposedly the __glXFindDRIScreen 'symbol' is defined in 'libGL.so', which I found in /usr/lib and /usr/lib/fglrx.  I remember people having to make symbolic links to /usr/lib/fglrx/libGL.so.1.2, and this seems to have resolved the problem for some people using fedora core 5: [http://www.fedoraforum.org/forum/archive/index.php/t-100136.html](http://www.fedoraforum.org/forum/archive/index.php/t-100136.html)
Quite a dirty fix, but apparently it worked for them, so I tried it.

However, after making the appropriate symlinks, and copying the appropriate kernel module files to /usr/lib (after making backups of course)... I still get the same error.  I notice that the people in that thread were getting a message stating that fglrx_dri.so was not found... but mine is that it won't load.

I guess it's back to using XP until this can get fixed for a bit, I can't use XGL/compiz with mesa, it's waaay too slow.

---

### Post by Freestyle Skater on 2006-09-23
Okay, I finally got my 3-D accleration working.  Well, actually, I didn't get it working so much as I let Ubuntu run it's automatic update.  I'm not sure exactly what it did, but when it updated my ati packages, they miraculously worked.  I'm not complaining.  So if you were having the same problem as me, running updates might be worth a shot.

x@x-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

---

### Post by graveson on 2006-09-23
what does this part of the guide mean and how do i go about doing this :
"Note: You have to recompile the kernel module after each kernel update!"

Help please

---

### Post by toasted on 2006-09-23
Where that is written, the compile code is just before that statement:

```
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```

When there is a kernel update, you have to run at least this once the kernel is installed and you have booted into it.

---

### Post by graveson on 2006-09-23
i think everything has worked ,but i have some strange issue . see link .Anyone has any ideas 
[http://paste.ubuntu-nl.org/24534](http://paste.ubuntu-nl.org/24534)

---

### Post by SledgeHammer_999 on 2006-09-23
Hi guys I have installed ati's 8.29.6 drivers using this guide and everything works fine. But I have a little problem concerning video playback. When I play a video with totem-gstreamer the colors are distorted. For example red is displayed as blue. But if I play the video using xine the colors are fine.
Does your gstreamer work fine with ati's drivers? or do you have similar problems to mine?

---

### Post by stoer on 2006-09-24
Hi,
may thanks for the guide, seems to work a treat.

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5946 (8.27.10)

glxinfo | grep rendering
direct rendering: Yes

fgl_glxgears
Using GLX_SGIX_pbuffer
2142 frames in 5.0 seconds = 428.400 FPS
2416 frames in 5.0 seconds = 483.200 FPS
2403 frames in 5.0 seconds = 480.600 FPS
2424 frames in 5.0 seconds = 484.800 FPS
2412 frames in 5.0 seconds = 482.400 FPS

---

### Post by Gio2k on 2006-09-30
Has anyone managed to get the ati driver (any version) installed and working on a machine with a Radeon Xpress 200m card?

So far, no matter what i install or how, i can't get opengl acceleration, and fglrxinfo always returns mesa as opengl renderer.

---

### Post by eternalsword on 2006-09-30
> **Gio2k said:**
> Has anyone managed to get the ati driver (any version) installed and working on a machine with a Radeon Xpress 200m card?

So far, no matter what i install or how, i can't get opengl acceleration, and fglrxinfo always returns mesa as opengl renderer.

do this from the terminal

cat /etc/X11/xorg.conf | grep vesa

if it returns something like

        Driver      "vesa"

then you'll need to first of all make a backup of xorg.conf so

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

then

sudo nano /etc/X11/xorg.conf

find the line with vesa as driver, and switch it to fglrx then

Ctrl-X to close
Y to tell it to save
Enter to complete

---

### Post by thecrazymonk86 on 2006-09-30
i got an error unable to open display :0 when i ran fglrxinfo

---

### Post by Gio2k on 2006-10-01
> **eternalsword said:**
> do this from the terminal

cat /etc/X11/xorg.conf | grep vesa

if it returns something like

        Driver      "vesa"

then you'll need to first of all make a backup of xorg.conf so

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

then

sudo nano /etc/X11/xorg.conf

find the line with vesa as driver, and switch it to fglrx then

Ctrl-X to close
Y to tell it to save
Enter to complete

Actually, i have fglrx as Driver in xorg.conf

```

sergio@sergio-laptop:~$ cat /etc/X11/xorg.conf | grep fgl
Driver      "fglrx"

```

I did almost everything on almost every thread i encountered.
One thing i cannot do is change the bios options for the ati card. My bios has no option for changing, so i guess i am stuck with Sideport + UMA. (128MB of each apparently, i don't know how to check that.)
Has anyone ever had any luck with installing an ATI xpress 200m with Sideport + UMA enabled?

---

### Post by eternalsword on 2006-10-01
> **Gio2k said:**
> Actually, i have fglrx as Driver in xorg.conf

```

sergio@sergio-laptop:~$ cat /etc/X11/xorg.conf | grep fgl
Driver      "fglrx"

```

I did almost everything on almost every thread i encountered.
One thing i cannot do is change the bios options for the ati card. My bios has no option for changing, so i guess i am stuck with Sideport + UMA. (128MB of each apparently, i don't know how to check that.)
Has anyone ever had any luck with installing an ATI xpress 200m with Sideport + UMA enabled?

I had fglrx set as driver as well, but there was another section with vesa.  Here was the two sections from my xorg.conf after following this tutorial.

```

Section "Device"
        Identifier  "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

```

I had to switch the driver in the first section from vesa to fglrx.

---

### Post by Gio2k on 2006-10-01
I have no other section. I edited my xorg.conf so that the only 'Device' section is the fglrx one.

---

### Post by dborquezm on 2006-10-02
Hi

fitzman49 says that the driver will work with all xseries cards, and he has  installed it for a 200M card, wich is officially supported as ATI says. Do you know if it'll work with a 200G ?

Thanks,
Daniel

---

### Post by eternalsword on 2006-10-06
> **Gio2k said:**
> I have no other section. I edited my xorg.conf so that the only 'Device' section is the fglrx one.

can you post that one section?

---

### Post by J-Gaming on 2006-10-07
I followed this guide, everything went smooth without errors..

But fglrxinfo still shows me mesa :(

Im new to linux also, so I dont know what to check or something..

---

### Post by FyreBrand on 2006-10-07
> **J-Gaming said:**
> I followed this guide, everything went smooth without errors..

But fglrxinfo still shows me mesa :(

Im new to linux also, so I dont know what to check or something..
It's highly likley you missed a small detail.  If you are absolutely sure you followed the procedure then you can edit your xorg.conf file, but I would try repeating the procedure just to make sure.  A few times I've done this while I was a little tired and I missed a small but crucial detail.

Here are a few things to pay especially close attention to:

1. Make sure your video card is in the list of supported video cards.  This is on ATI's website and is dependent on which driver version you downloaded.

2. Make sure you have the alternate repositories enabled.  Ubunutu Demon's recommended sources.list (in the Customization Guide section) is a really good thread.  It describes how to enable other software repositories that can be important to tasks such as installing ATI's proprietary driver.  It can be found here: [**Ubuntu Demon's Recommended sources.list**]("http://www.ubuntuforums.org/showthread.php?t=185758").

3. Either cut and paste the code entries into your terminal or ensure you there are absolutely no typing errors.  You can ctrl-c to copy from the code window and use the middle mouse button or ctrl-insertkey to paste into your terminal.

4. When you are making and building the deb packages make sure you are in the same directory as the ati-driver-install-version.bin file and that you have no older .deb files for xorg and fglrx which are created when you make the package.  If you have old ones, then make sure you delete them or move them to a backup folder.  Just make sure they aren't in the folder you're working in.

5. If you have ever installed fglrx before and configured your xorg.conf file you will either need to edit it manually or use the --force option when you initialize the file.  So the code would look something like this:
```
sudo aticonfig --force --initial
```
I'm fairly confident that is the right syntax but I'm also fairly new so make sure you double check in the help file.  It shows how to enter the option.

6. Make sure you reboot.

If that doesn't work then read over this thread and gather the kind of output that more knowledgeable people request and post it back here.  This wold include your xorg.conf file, but also might include the output of *glxinfo* from the terminal.

Good luck.

edit:  I forgot something.  Sometimes for reasons I don't really understand the fglrx modules don't get disabled like they're supposed to.  If you have done everything properly but still get mesa drivers when you check fglrxinfo at the terminal, then try manually disabling the Ubuntu provided fglrx.  These are the steps:
> /!\ Whether you install manually or from dapper-seveas, you MUST disable the Ubuntu-provided fglrx by performing these actions: 
 Disable fglrx in /etc/default/linux-restricted-modules-common 
 Run sudo /sbin/lrm-manager 
 Run sudo depmod -a 
 Reboot
I got this from this Help Article on the Ubuntu Help site: [**BinaryDriverHowTo/ATI**]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

To be specific on how to disable the Ubuntu provided fglrx --
1. Open the file as sudo in your editor of choice (gedit, kwrite, kate, scite, etc).  I like nano because I don't have to leave the terminal and it's pretty easy to use.
```
sudo nano /etc/default/linux-restricted-modules-common
```

There will be a few notes in the comment section and then if your file is like mine it will have one uncommented line that says:
```
DISABLED_MODULES=""
```
You will want to insert fglrx between the quotes like this:
```
DISABLED_MODULES="fglrx"
```
If there is anything else already between those quotes leave them there unless you know what you're doing.  Make sure your entry is separated by a white space from any other entry.  The comment section in the file provides an example.

2. Next execute the last two commands.  Honestly I don't know what they do, but I followed the instructions.
```
sudo /sbin/lrm-manager
sudo depmod -a
```

3. Next reboot.

I put this in because on my Ubuntu 6.06 install I don't have to do this, but on my Kubuntu 6.06 partition I do have to do this.  I'm not really sure why there is a difference because the cores are the same, but I have to do it this way.

---

### Post by jinxen on 2006-10-09
I have got a x1300 card on my laptop, and im not able to get DRI work. I use the newest driver 8.29.6. I have disabled Composite, still no luck. Should i try the 8.27.10 driver instead?

---

### Post by Karbonik on 2006-10-16
So far no worky on my (rented) 
HP dv5000 
Kernel 2.6.15-27-amd64-generic
KDE: 3.5.2
Radeon Xpress 200M


 
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release.gpg
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:2 [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) dapper-pouit Release.gpg [189B]
Get:3 [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release.gpg [189B]
Get:4 [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) dapper-pouit Release [26.6kB]
Hit [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper/flash Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) dapper-pouit/backports Packages
Hit [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) dapper-pouit/contrib Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:11 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages [14B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 26.7kB in 6s (4177B/s)
Reading package lists... Done
karbonik@biosoalr-laptop:~/admin$ sudo apt-get install module-assistant build-essential
Reading package lists... Done
Building dependency tree... Done
module-assistant is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karbonik@biosoalr-laptop:~/admin$ sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
dh-make is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
gcc-3.3-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karbonik@biosoalr-laptop:~/admin$ chmod +x ati-driver-installer-8.26.18-x86_64.run
karbonik@biosoalr-laptop:~/admin$ ./ati-driver-installer-8.26.18-x86_64.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.26.18...........................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/dapper
/tmp/fglrx.d8BgjT ~/admin/fglrx-install
Package /home/karbonik/admin/xorg-driver-fglrx_8.26.18-1_amd64.deb has been successfully generated
Package /home/karbonik/admin/xorg-driver-fglrx-dev_8.26.18-1_amd64.deb has been successfully generated
Package /home/karbonik/admin/fglrx-kernel-source_8.26.18-1_amd64.deb has been successfully generated
Package /home/karbonik/admin/fglrx-control_8.26.18-1_amd64.deb has been successfully generated
Package /home/karbonik/admin/fglrx-sources_8.26.18-1_amd64.deb has been successfully generated
~/admin/fglrx-install
Removing temporary directory: fglrx-install
karbonik@biosoalr-laptop:~/admin$ sudo dpkg -i xorg-driver-fglrx_8.26.18-1_amd64.deb
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 121695 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.26.18-1_amd64.deb) ...
Setting up xorg-driver-fglrx (8.26.18-1) ...
Starting atieventsd: done.

karbonik@biosoalr-laptop:~/admin$ sudo dpkg -i fglrx-kernel-source_8.26.18-1_amd64.deb
Selecting previously deselected package fglrx-kernel-source.
(Reading database ... 121810 files and directories currently installed.)
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.26.18-1_amd64.deb) ...
Setting up fglrx-kernel-source (8.26.18-1) ...
karbonik@biosoalr-laptop:~/admin$ sudo dpkg -i fglrx-control_8.26.18-1_amd64.deb
Selecting previously deselected package fglrx-control.
(Reading database ... 121814 files and directories currently installed.)
Unpacking fglrx-control (from fglrx-control_8.26.18-1_amd64.deb) ...
Setting up fglrx-control (8.26.18-1) ...

karbonik@biosoalr-laptop:~/admin$ sudo rm /usr/src/fglrx-kernel*.deb
rm: cannot remove `/usr/src/fglrx-kernel*.deb': No such file or directory
karbonik@biosoalr-laptop:~/admin$ sudo module-assistant prepare
Getting source for kernel version: 2.6.15-27-amd64-generic
Kernel headers available in /usr/src/linux

Done!
karbonik@biosoalr-laptop:~/admin$ sudo module-assistant update

Updated infos about 70 packages
karbonik@biosoalr-laptop:~/admin$ sudo module-assistant build
No package specified. STOP.
karbonik@biosoalr-laptop:~/admin$ sudo module-assistant build fglrx
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Done with /usr/src/fglrx-kernel-2.6.15-27-amd64-generic_8.26.18-1+2.6.15-27.48_amd64.deb .
karbonik@biosoalr-laptop:~/admin$ sudo module-assistant install fglrx
Selecting previously deselected package fglrx-kernel-2.6.15-27-amd64-generic.
(Reading database ... 121821 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.15-27-amd64-generic (from .../fglrx-kernel-2.6.15-27-amd64-generic_8.26.18-1+2.6.15-27.48_amd64.deb) ...
Setting up fglrx-kernel-2.6.15-27-amd64-generic (8.26.18-1+2.6.15-27.48) ...

karbonik@biosoalr-laptop:~/admin$ sudo depmod
karbonik@biosoalr-laptop:~/admin$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
karbonik@biosoalr-laptop:~/admin$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
karbonik@biosoalr-laptop:~/admin$    



/etc/default/linux-restricted-modules is set to  "" currently.

The problem is that I still get Black Screen Of Despair at launch of kdm.

Haven't tried the BIOS thing yet - is that necessary?

---

### Post by Karbonik on 2006-10-16
Ok, so I tried the BIOS thing - UMA+Sideport

0 MB  - Black Screen
32 MB - Black Screen
64 MB - Black Screen
128 MB - Works, sortof...  launches kdm, and then promptly freezes everything and locks.  Not even mouse movement.

Here be the xorg.conf that does NOT work:

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
#	InputDevice    "Synaptics Touchpad"
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

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "UseFBDev" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
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



Any ideas?

---

### Post by nweaver916 on 2006-10-26
ARGGHHH!!!


now that I have that out....

I have a Dell Latitude D810 with ATI M300 card. 

Updated to Edgy today, and trying to get the drivers to work (want to try some of that new eye candy)


I have tried everything I can find from these forums, and NOTHING leads to fglrxinfo showing anything but the mesa driver. 


Current xorg.conf 
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
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
	FontPath     "/usr/share/fonts/X11/misc"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
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

Currently have fglrx blocked in the restricted modules file

glxinfo:

```
nickw@lappy386:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```


when I unblock fglrx in the restricted modules, is shows up in an lsmod, but the fglrxinfo still shows as mesa drivers. 

Any hope for me? I'm about to backup/rebuild edgy from scratch.

---

### Post by FyreBrand on 2006-10-26
If you followed the instructions of the first post, or the instructions in the Ubuntu Help site and installed the ATI proprietary driver (that you downloaded from their site) then you should disable fglrx in the module not enable it.  See post 336 above for more.

Whether that is enabled or not depends on what drivers you install.  Also before you use the proprietary driver from the ATI site make sure that your card is supported in that version.  They have a list of supported cards on their site.

---

### Post by Rob_H on 2006-10-27
Argh! I have one of the dreaded Xpress 200M cards on an HP Pavilion dv8000. I had it working with the "fglrx" driver in Dapper, as long as I used version 8.24.8 and enabled UMA in the BIOS.

Well, today I upgraded to Edgy and now the 8.24.8 driver no longer works. (Recompiling the kernel module failed.) If I use the version of the driver included in Edgy, I have to disable DRI or else I get the frozen black screen when starting X.

Does anyone with a Pavilion dv8000 have 3D acceleration working under Edgy? Any pointers would be greatly appreciated! I really hate this card.

---

### Post by nweaver916 on 2006-10-27
> **FyreBrand said:**
> If you followed the instructions of the first post, or the instructions in the Ubuntu Help site and installed the ATI proprietary driver (that you downloaded from their site) then you should disable fglrx in the module not enable it.  See post 336 above for more.

Whether that is enabled or not depends on what drivers you install.  Also before you use the proprietary driver from the ATI site make sure that your card is supported in that version.  They have a list of supported cards on their site.

I have tried both ways, and every way. I think I'm going to backup my /home directory and go at it with a fresh install of Edgy (instead of my update from dapper)

Can I just say...I hate ATI

---

### Post by flapane on 2006-10-28
Yes, you aren't the only one who hates ati...

[[IMG]http://img132.imageshack.us/img132/8862/sk8ey1.th.jpg[/IMG]](http://img132.imageshack.us/img132/8862/sk8ey1.jpg)
...this only to show you how I am happy after having trown my X800GT out of the windows yesterday after 16MONTHS OF FGLRX TROUBLES and having enabled 3d on my new 7800gt in 1,5hours!! 16months against 1,5hours!
And in 16months fglrx was active only for one day, the next day it broken itself!! omg
god bless nvidia
p.s do someone want to buy my x800gt?:mrgreen:

---

### Post by weematt on 2006-11-02
In an effort to continue to try to convince ATI/AMD to fix this problem, I just sent this to their support team (see below).  If you want this problem fixed - please take the 5 mins to complain to ATI/AMD.

-------------------------

As I am sure you are aware, the Radeon 200M has very poor linux driver support. There is a large community of users that is very frustrated with this situation (and has been for years now!).

Please do not dismiss this ticket with a "we do not support your product" email. This is an ATI product which ATI have claimed to support -- but have in fact failed to do so. Perhaps now that AMD is in charge, the frustrated community to which I refer above can hope for a change for the better? ie - they perhaps can hope that the next driver release will support the 200M properly.

Here is an example of the kinds of comments you can see all over (if you do a google-search for 200M linux fglrx driver):

"...this only to show you how I am happy after having trown my X800GT out of the windows yesterday after 16MONTHS OF FGLRX TROUBLES and having enabled 3d on my new 7800gt in 1,5hours!! 16months against 1,5hours!
And in 16months fglrx was active only for one day, the next day it broken itself!! omg
god bless nvidia
p.s do someone want to buy my x800gt?"

FROM: [http://www.ubuntuforums.org/showthread.php?t=204910&page=35](http://www.ubuntuforums.org/showthread.php?t=204910&page=35)

That's on page 35(!) of that forum! Does AMD/ATI want to maintain competition with nvidia? If so, you better get busy making us customers happy!

Thanks for your time. I don't mean to be an ***, I'm just frustrated (like alot of others).

Cheers,

Matt

---

### Post by zophiel on 2006-11-04
with HP&#12288;dv8000&#12288;and the ever-so-friendly-200M Express (5955)

I just rolled back to dapper and installed the 8.24.8-x86 driver and DRI work wonderfully well.

---

### Post by mikael_b on 2006-11-05
When i try to follow the how-to, I get this error>

> ./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.26.18..................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 163: Syntax error: Bad substitution
Removing temporary directory: fglrx-install


What should i do?

Btw, I run edgy.

---

### Post by lorddaddy84 on 2006-11-06
It worked, thanks. Now let me see if it hangs up on reboot.

---

### Post by fpeixoto on 2006-11-09
> **mikael_b said:**
> When i try to follow the how-to, I get this error>



What should i do?

Btw, I run edgy.

I'm having exactly the same issue right now with a 9600

---

### Post by AceRimmer on 2006-11-11
edit.  Got the driver working.

---

### Post by chopz on 2006-11-14
> **mikael_b said:**
> When i try to follow the how-to, I get this error>



What should i do?

Btw, I run edgy.

I was getting this error too.  I found some other thread (sorry lost the link) where the solution was to force the installer to use bash instead of sh.  

so I ran this command and it got farther than before but errored out as seen below

chopz@xxxxxx:~$ sudo bash ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.27.10......................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/edgy
Requested package is not supported.
Removing temporary directory: fglrx-install

 ](*,) ](*,) ](*,)

---

### Post by kybKenny on 2006-11-17
I found a post here: [http://blog.computer-tipps.info/2006/10/15/ati-treiber-unter-edgy-eft/]("http://blog.computer-tipps.info/2006/10/15/ati-treiber-unter-edgy-eft/")

it's in german, but you should be able to read the code ;) 

in essence, it says that you have to indeed change your shell from dash to bash, and then you run the installer script and it should run through.

So, chopz, i think you can circumvent your error by downloading a newer version of the driver, not? I tried it with 8.29.6 and it worked...

---

### Post by poebae on 2006-11-18
Hey guys,I need some help. I'm new to Ubuntu, so please bear with me.

I (thought) I got my ATI card working properly, but there's a problem:

I was fiddling around with my xorg.conf, and when I tried rebooting I got the error message that my GUI session couldn't be started.

I fiddled around with my xorg.conf again and typed 'startx', then pulled up a terminal, and my fglrxinfo output showed the correct ATI stuff instead of MESA. Then I realised that I wasn't logged in 'properly', in that when I pressed "Quit", the 'shut down' and 'restart' options weren't available to me.

When I rebooted my system and logged in again, I was given the "Couldn't open screen 0" message.

Why does my card work properly only when my Ubuntu doesn't boot up correctly and I have to type 'startx' manually?

---

### Post by RobNyc on 2006-11-20
I didn't follow all that but I just followed the ati-installer instructions and noticed now my ATI Control Panel doesn't work and fglrxinfo inputs 

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

But I have 3d and proper resolution though

but I was trying this and when I was doing bash ati-driver* line I got

Generating package: Ubuntu/edgy
[: 182: ==: unexpected operator
./packages/Ubuntu/ati-packager.sh: 182: pushd: not found
Package build failed!
Package build utility output:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
./packages/Ubuntu/ati-packager.sh: 182: popd: not found
Removing temporary directory: fglrx-install

---

### Post by xtlosx on 2006-11-20
anyone know why i would be having this problem with the x86_64 installer?

-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 156: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

---

### Post by nova- on 2006-11-24
Hi!

please see the recently updated article here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by abmorissun on 2006-12-02
Please note that after a clean install of Ubuntu 6.1, you'll have a Terminal application that uses /bin/dash by default. If you try to run the ATI driver install with /bin/dash, you'll get a *bad substitution*. This is **simple to fix** (although it took me about 12 hours to hunt this down).

In Terminal, click "Edit"->"Current Profile..."

On the "Title and Command" tab, under the "Command" section, select "Run a custom command instead of my shell".

Enter **/bin/bash** beside "Custom command:"

Close the dialog and restart your Terminal. Now the ATI driver install won't get a bad substitution.

---

### Post by kcallis on 2006-12-07
In am running a HP dv8040us, and Edgy with kernel 2.6.19. The building of the debs are great, but when I try to do module-assistant build,install fglrx, the process stops with a something this

 touch configure-stamp                                                      &#9618; 
 &#9474; dh_testdir                                                                 &#9618; 
 &#9474; /usr/bin/make -C /lib/modules/2.6.19/source                                &#9618; 
 &#9474; SUBDIRS=/usr/src/modules/fglrx modules                                     &#9618; 
 &#9474; make[1]: Entering directory `/usr/src/linux-2.6.19'                        &#9646; 
 &#9474;   CC [M]  /usr/src/modules/fglrx/firegl_public.o                           &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:89:26: error: linux/config.h: No    &#9618; 
 &#9474; such file or directory                                                     &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:456: warning: initialization from   &#9618; 
 &#9474; incompatible pointer type                                                  &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function ‘firegl_stub_open’:    &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:579: warning: assignment discards   &#9618; 
 &#9474; qualifiers from pointer target type                                       

So, what should be my net move? ](*,)

---

### Post by ripgut on 2006-12-11
> **xtlosx said:**
> anyone know why i would be having this problem with the x86_64 installer?

-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 156: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

I'm getting the same thing. Can someone please help?

---

### Post by bladez90 on 2006-12-16
> **ripgut said:**
> I'm getting the same thing. Can someone please help?

its because of the "--buildpkg Ubuntu/dapper", you need to change it to "--buildpkg Ubuntu/edgy".  try that...

---

### Post by Popoi on 2006-12-21
> **nova- said:**
> Hi!

please see the recently updated article here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

:oops: :oops: :oops: :oops: 
=D> =D> =D> =D> 

It works!! At last.. so many time waiting Edgy ti this.. it's a miracle. Nice!

(Edgy Eft x64, Radeon X1300 Pro)

---

### Post by imrazor on 2006-12-22
Just upgraded to a Radeon X1800GTO from a Geforce 6600GT. According to the Xserver log, I've successfully built and installed the fglrx kernel module. with the 8.32.5 installer. However, the GLX extension module will not build. When I run module-assistant I get the following error:

Warning, /usr/src/linux-source-2.6.15 seems to contain unconfigured kernel source!

I've checked a few other threads, and verified that I have config.h and autoconf.h files in the correct location. Despite this error, module-assistant appears to continue building the modules (except the glx), and X seems to be loading the fglrx module successfully. 

As an addititional note, the Xv overlay doesn't appear to be working either, so full screen video output looks very ugly.

I suspect the problem is some left over files from my Nvidia setup (which had the proprietary drivers loaded.) If I can't find a good answer here, I think I'm going to blow away my Linux partition, install Edgy, and get a clean start.

---

### Post by boom1992 on 2006-12-25
Hello, theres a problem with DRI on my fglrx-driver:
I have a x1600pro
fglrxinfo:
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
There`s my xorg.conf:
[http://www.ubuntuusers.de/paste/6144/](http://www.ubuntuusers.de/paste/6144/)

And there my Xorg.0.log:
[http://www.ubuntuusers.de/paste/6146/](http://www.ubuntuusers.de/paste/6146/)

This here is the error:
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
1010 (EE) fglrx(0): cannot init AGP
1011 (II) fglrx(0): [drm] removed 1 reserved context for kernel
1012 (II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7129000
1013 (WW) fglrx(0): ***********************************************
1014 (WW) fglrx(0): * DRI initialization failed! *
1015 (WW) fglrx(0): * (maybe driver kernel module missing or bad) *
1016 (WW) fglrx(0): * 2D acceleraton available (MMIO) *
1017 (WW) fglrx(0): * no 3D acceleration available *
1018 (WW) fglrx(0): ********************************************* *
Can you help me???

---

### Post by manutdfan2850 on 2006-12-25
hi i have been trying to install my Ati drvers. I have a laptop with ATI Mobility Radeon 9000. I downloaded the package on the ATI website. I made the package "executable" and double clicked it. I clicked "run in terminal" because nothing else seemed to work. 

Here is what i got. (see screenshot). I dont know what this means. Please advise.

Thanks. I am a complete noob by the way. 

[[IMG]http://img76.imageshack.us/img76/522/atiinstall2tv9.th.png[/IMG]](http://img76.imageshack.us/my.php?image=atiinstall2tv9.png)

---

### Post by Mateo on 2006-12-28
i'm trying to go through the guide, but when i go to the ATI site and try to get the drivers, this is what starts downloading:

ati-driver-installer-8.32.5-x86.x86_64.run

but i don't have a 64 bit processor.  I didn't select the 64 bit one either.  i'm afraid to continue on.  guessing must be a website malfunction.

---

### Post by IanW on 2006-12-28
Mateo - that's the correct file.

ATI merged their 32 and 64 bit installers into a single program.
Just follow the guide using that file, you'll be fine.

---

### Post by Nafanja on 2007-01-03
I have reproduced the procedure described [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  with the new 8.32.5 driver on my 64bit PC. It works, however when running fglrxinfo it recognizes the card as "Generic", while I have X1300 Pro.
>  fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.6234 (8.32.5)
  
I am happy, since it is definitely an improvement..., but I will appreciate any suggestions on how to make the system to recongize my card properly.
Many thanks.

---

### Post by Absurd on 2007-01-06
Good evening everyone.

Well, I've recently been compiling a custom kernel (due to boredom) and everything seems fine except that I can't get direct rendering to work.

when I enter "$ fglrxinfo" it tells me

> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

and when I enter "$ glxinfo | grep direct" I get 

> direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

I have the xorg-driver-fglrx installed and direct rendering works fine with the regular Ubuntu kernel.

So I'm wondering if anyone knows how I can get it working with a custom kernel.

[edit] sorry for posting this in the wrong place. please delete

---

### Post by subliminal on 2007-01-09
I'm on an Xpress 200M and like many I had the mesa probelm. I solved this by re-installing the driver. This time I added the section about extensions and turning composite off to my xorg.conf. This is clearly a very important step, up to now I assumed as I had no such section it would be off, how very wrong I was. This was what did it for me I. Also from [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")
I did 
```
sudo mkdir /usr/X11R6/lib/modules
sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/
```

Then the re-install, firstly removing all the deb packages that had been created, there was a dependency issue here relating to an older file, which I also uninstalled, then re-installed all the deb files (basically doing the whole thing again apart from the download and extraction).

And now it works, not very fast mind, but it works.

---

### Post by nabdan on 2007-01-09
Hi all,

same error than a few post ago

nab@nab-desktop-2:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.6234 (8.32.5)


Someone knows how fix it ?

thanks in  advance :)

Bye

---

### Post by nabdan on 2007-01-10
Hi again :)

More info about trouble, i hope it can help.

> nab@nab-desktop-2:~$ dmesg | grep fglrx
[17179614.796000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[17179614.796000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179616.244000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[17179616.252000] [fglrx] total      GART = 134217728
[17179616.252000] [fglrx] free       GART = 118226944
[17179616.252000] [fglrx] max single GART = 118226944
[17179616.252000] [fglrx] total      LFB  = 260960256
[17179616.252000] [fglrx] free       LFB  = 250474496
[17179616.252000] [fglrx] max single LFB  = 250474496
[17179616.252000] [fglrx] total      Inv  = 0
[17179616.252000] [fglrx] free       Inv  = 0
[17179616.252000] [fglrx] max single Inv  = 0
[17179616.252000] [fglrx] total      TIM  = 0


> nab@nab-desktop-2:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7183


> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
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
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
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

Section "Extensions"
        Option      "Composite" "disable"
EndSection


Thanks for helping :)

Bye !

---

### Post by compholio on 2007-01-10
> **nabdan said:**
> Driver "vesa"

I don't know about any other problems, but that needs to be "fglrx".

---

### Post by nabdan on 2007-01-11
ohhh

I thougth it was required only in second section:

> Section "Device"
Identifier "ATI Technologies, Inc. ATI Default Card"
Driver "[COLOR="red"]vesa[/COLOR]"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "[COLOR="Red"]fglrx[/COLOR]"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection

Thanks a lot Compholio, I wil le you know if it works :) .


Bye !

NabdaN

---

### Post by compholio on 2007-01-12
It probably wouldn't matter if the first one didn't exist - but since it's specified with:
BusID "PCI:1:0:0"
The card resource is likely gobbled up by the vesa driver so the fglrx driver can't use it.

---

### Post by nabdan on 2007-01-13
Hi Compholio,

Thanks for explanation.

I really appreciate it.

I have messed up my install, I need to restart from scratch, but I will let you know if it works.

Bye !

---

### Post by firstc624 on 2007-01-14
so do i follow this guide exactly now?  or is this now outdated?  i have a 200m on a laptop and looking for a fix

thanks for response  :-)

---

### Post by xtlosx on 2007-01-19
I have some even stranger problems... I had a fresh install......this is what happened fellas, help me please!

I have a radeon x1300 mobility.... i went through your guide, all the way through, no errors.. when i reboot, the gdm login screen looked like it had improved a lot. the resolution was noticeably nicer.... i enter login, and password, i hit enter, the password field greys out... the login jingle plays, and the computer stops... completely.......
what is going on?!?!

---

### Post by nighthawke on 2007-01-20
I'm doing alot of nut-busting here as well in trying to get 3D to operate dependably. My 9600XT keeps choking up on running OpenGL 3D apps.

6.10 with full updates, current FGLRX drivers.

FGLRXINFO yields this:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6286 (8.33.6)

GLXINFO grep yields this too:
direct rendering: yes



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
	FontPath     "/usr/share/fonts/X11/misc"
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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
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
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
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

Section "Extensions"
	Option	    "Composite" "0"
EndSection



Any ideas?

---

### Post by spacetree on 2007-01-25
I followed the steps, and everything seems allright... except for this:

I cannot use my openGL screen savers an many applications cannot find the library libGL.so.1 before this i was able to use googleearth, and now i cant. The library exist, (i asked to locate)...

Somoeno has an idea?

---

### Post by SexyStud on 2007-01-25
Hello,

I installed the latest ATI drivers from the official website following the Ubuntu Wiki tutorial. Everything apparently went OK, but when I fglrxinfo, I get some mesa drivers refered, instead of my graphic card (which is ATI Mobility Radeon 9700). Also, I have direct rendering OFF. I need it ON for Beryl. How can I fix this?

---

### Post by no24 on 2007-01-25
This needs to be added to the xorg.conf file to rid the mesa problem
```

Section "Extensions"
	Option "Composite" "false"
EndSection
```

---

### Post by Mortiferous on 2007-01-26
Hi, I'm installing the latest ATI driver (8.33.6) and I'm going through the BinaryDriverHowto/ATI article. Would someone please explain this step to me in more detail?
> Modifying xorg.conf

When you install from ati.com drivers or the dapper-seveas repository, you still need to change xorg.conf and add the fglrx module to /etc/modules as described under "Ubuntu provided drivers". There are scripts from ATI that may or may not work for you. They will backup xorg.conf before modifying it. 

I'm using Edgy with an ATI X1650 Radeon. I can't find a section called "Ubuntu provided drivers" and I've already blacklisted the fglrx module.

---

### Post by SexyStud on 2007-01-26
> **no24 said:**
> This needs to be added to the xorg.conf file to rid the mesa problem
```

Section "Extensions"
	Option "Composite" "false"
EndSection
```


When I do this, Gnome doesn't work. It freezes before the splash screen. Any other clues?

---

### Post by compholio on 2007-01-27
Try adding this to the ServerFlags section of xorg.conf:
Option "AIGLX" "false"

Edgy comes with XOrg 7.1, which has AIGLX (which is incompatible with the Binary blob from what I've heard).

---

### Post by whistlerspa on 2007-01-28
When i try this method i get the following b******t in the first install process

 **** :~/Downloads$ ./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.26.18..................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 163: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
rick@RIX-AMD:~/Downloads$ ./ati-driver-installer-8.26.18-x86.run --buildpkg
Makeself version 2.1.3 
 1) Getting help or info about ./ati-driver-installer-8.26.18-x86.run :
  ./ati-driver-installer-8.26.18-x86.run -h|--help                     Print this message
  ./ati-driver-installer-8.26.18-x86.run -i|--info                     Print embedded info : title, default target directory, embedded script 
  ./ati-driver-installer-8.26.18-x86.run -l|--list                     Print the list of files in the archive
  ./ati-driver-installer-8.26.18-x86.run -c|--check                    Checks integrity of the archive
  ./ati-driver-installer-8.26.18-x86.run --extract NewDirectory        Extract this package to NewDirectory only
 
 2) Running ./ati-driver-installer-8.26.18-x86.run :
  ./ati-driver-installer-8.26.18-x86.run [options] [additional arguments to embedded script] with following options (in that order)
  --keep                           Do not erase target directory after running the embedded script
  Following arguments will be passed to the embedded script:
  --install                        Install the driver(default)
  --listpkg                        List all the generatable packages 
  --buildpkg package               Build "package" if generatable ("package" as returned by --listpkg)
rick@RIX-AMD:~/Downloads$ ./ati-driver-installer-8.26.18-x86.run --buildpkg package
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.26.18..................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
**./ati-installer.sh: 163: Syntax error: Bad substitution**
****:~/Downloads$ 

What the **** is **'bad substitution'**

---

### Post by whistlerspa on 2007-01-28
I can't get the installation to work using this method i get a 'file substitution' error  - whatever that means. Now after some beryl updates this a.m the whole desktop is stuck on one desktop only and the menus do not display properly. 

I've been unhappy with my ATI Radeon 9600 card for some time. It is unpredictable and flaky with it's performance. Think I'll just flag beryl for this computer. It works fine on my Intel laptop however.

---

### Post by SexyStud on 2007-01-29
> **compholio said:**
> Try adding this to the ServerFlags section of xorg.conf:
Option "AIGLX" "false"

Edgy comes with XOrg 7.1, which has AIGLX (which is incompatible with the Binary blob from what I've heard).

I do this and get the same problem with "Composite" option: Gnome doesn't load - stops right before the splash screen.

Something I noticed though: I can know when Gnome will fail to load because in those situations, I get the "login" sound - the one that sounds right before you put your username/password - played twice. When Gnome works normally, the sound was only played once.

---

### Post by commonplace on 2007-01-30
> **nova- said:**
> Hi!

please see the recently updated article here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

FINALLY!! I've been working on getting my ATI Radeon X700 PCIe 256MB card working since.. well, since I've been using Linux back on Fedora Core 5. Almost a year now. This is the first time I've gotten 3D acceleration to work. I followed the guide's instructions on installing the latest drivers from ATI, and that worked perfectly. I had tried dozens and dozens (if not hundreds) of fixes and tips and guides, and nothing worked until this. Thanks!

/Kevin

---

### Post by compholio on 2007-02-06
> **SexyStud said:**
> I do this and get the same problem with "Composite" option: Gnome doesn't load - stops right before the splash screen.

Something I noticed though: I can know when Gnome will fail to load because in those situations, I get the "login" sound - the one that sounds right before you put your username/password - played twice. When Gnome works normally, the sound was only played once.

My understanding is that both composite and AIGLX must be disabled, if you disable just one or the other then you will likely have problems.

---

### Post by SexyStud on 2007-02-07
I tried with both AIGLX and Composite disabled, and I still get the same problem: Ubuntu boots, I log in, but right after that nothing happens. Brown screen from Ubuntu background, I can move the mouse, but nothing happens.

Here are my files for reference, click to open. Maybe I am doing something wrong and the logs can show it:

[Actual xorg.conf - works fine but no direct rendering](http://thiago.home.sapo.pt/xorg.conf.txt)
[Xorg.0.log of the actual xorg.conf above](http://thiago.home.sapo.pt/xorg.log.aiglxOFF.compositeON.txt)
[Xorg.0.log when I turn Composite off](http://thiago.home.sapo.pt/xorg.log.aiglxOFF.compositeOFF.txt)


I don't have a clue of what might be happening. Any help or lights would be appreciated, as I want to have beryl working. Also, I think this problem is interfering with other applications, Google Earth more specifically.

---

### Post by Kevf on 2007-02-08
Error: need root permissions or the `fakeroot' package installed

Someone?

---

### Post by Kevf on 2007-02-10
Whoe It worked (got the fakeroot package installed)!! But when Grub loads I see two kernels (I've got a dual boot with xp). The one that loads on default works, But is there anything I should do about the other? Futhermore I have to recompile the kernel after each update. Meaning?

---

### Post by SpikeyMike on 2007-02-11
Hi, I followed the procedure by Fitzman to install the 8.26,18 drivers and it went ok until I got to the Install .deb packages  part, then it said that it couldn't find the directory.  Also I have the ATI Radeon X700,  is it best to use the 8.26.18 drivers or the newer 8.27.10 drivers or maybe even the linux proprietary drivers? any help appreciated

Spikey

---

### Post by dracomordag on 2007-02-11
i'm not allowed to edit sources.list

how do i give myself permissions to do so?

---

### Post by commonplace on 2007-02-11
> **dracomordag said:**
> i'm not allowed to edit sources.list

how do i give myself permissions to do so?

Use sudo (and then enter your password) before the gedit (or whatever) command. You can also use the GUI if you're not comfortable doing it (System | Administration | Software Sources, then go to the Third Party tab, click the 'Add' button, and paste in (only one can be done at a time) the first repo; then repeat for any additional repos.

/Kevin

---

### Post by dracomordag on 2007-02-11
what?

i need to edit the sources.list file to

"Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps."

---

### Post by commonplace on 2007-02-11
Okay, then just go to System | Administration | software Sources, and make sure all the boxes on the first tab are checked (namely, the ones that say 'universe' and 'multiverse' in parentheses at the end). That's it. Hit 'Close' and it'll probably ask you to reload; go ahead and do that, and you're set. Continue on with whatever instructions you're following.

/Kevin

---

### Post by dracomordag on 2007-02-11
chmod: cannot access 'ati-driver-installer-8.27.10.x86_64.run': No such file or directory

---

### Post by dracomordag on 2007-02-11
david@desktop:~$ ./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.27.10......................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 156: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
david@desktop:~$

---

### Post by dracomordag on 2007-02-11
anyone?

---

### Post by mr.f on 2007-02-12
> **dracomordag said:**
> david@desktop:~$ ./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.27.10......................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 156: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
david@desktop:~$

I ran into the same problem, and it turned out the reason was that the default shell in edgy is dash, not bash like in previous Ubuntu versions. dash is a light-weight shell but does not have all the features of bash.

So, the solution is to replace the  /usr/bin/sh from a symlink to dash to a symlink to bash, start a new shell, and retry the installer script.

Also, I found a more up-to-date ATI driver install howto for Edgy here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by Kevf on 2007-02-14
Still no luck. Still running on mesa :( 

What does the last command do?

---

### Post by maddentim on 2007-03-12
Hello, 

I have an ATI Radeon 9250 card in my machine running ubuntu 6.10.  I have two LCD monitors with both DVI and analog connections.  The card has one of each.  I want it set up with one desktop across both monitors.  I have gotten both the open driver with mergedfb and the closed ATI driver with big desktop working for the most part.  I was having issues with the open driver with more complex graphics.  It would go black at times, so I tried the closed ATI driver.  It has been better with just two issues that I would like to solicit advice on if someone happens to know what to try.

1 - With ATI proprietary driver and big desktop, when I move the cursor on the main screen to the right, then video playing on tvtime or democracy slides out of its window to the left.  If move the screen to the left side of the left hand montior, the video comes back into the window.  

2 - With ATI proprietay drive and big desktop, I would like to make my main monitor 1280x1024, while the second monitor is at 1024x768.  I can't seem to get it to work with different resolutions.  Any help here would be great.

3 - I am perfectly willing to go back to the open driver, but for this blacking out of part of the video.  I think it has something to do with the 3D which I had to struggle to get going on both.  It effects screen savers and google earth images when zoomed in close...

Here is my xorg.conf...

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
	Option	    "AIGLX" "off"
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
	FontPath     "/usr/share/fonts/X11/misc"
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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
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
	Identifier   "COMPAQ FS740"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps"
#	Option	    "Mode2" "1024x768" #Resolution for second monitor
#	Option	    "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
#	Option	    "HSync2" "65" #This sets the horizontal sync for the secondary display. 
#	Option	    "VRefresh2" "60" #This sets the refresh rate of the secondary display.
	Option      "CenterMode" "off"

	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "ForceMonitors" "tmds1,crt1"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor    "COMPAQ FS740"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
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

Section "Extensions"
	Option	    "Composite" "false"
EndSection

Thanks, Tim

Thanks for any help that you can provide!

Thanks
Tim

---

### Post by nabdan on 2007-03-13
Hi all,

All seems perfect now but still an error :

```
nab@nab-desktop-2:~$ dmesg | grep fglrx
[17179614.796000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[17179614.796000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[COLOR="Red"][17179616.244000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)[/COLOR]
[17179616.252000] [fglrx] total GART = 134217728
[17179616.252000] [fglrx] free GART = 118226944
[17179616.252000] [fglrx] max single GART = 118226944
[17179616.252000] [fglrx] total LFB = 260960256
[17179616.252000] [fglrx] free LFB = 250474496
[17179616.252000] [fglrx] max single LFB = 250474496
[17179616.252000] [fglrx] total Inv = 0
[17179616.252000] [fglrx] free Inv = 0
[17179616.252000] [fglrx] max single Inv = 0
[17179616.252000] [fglrx] total TIM = 0
```

anyone knows something about this bug ?

All is working but performances are not so good.

Bye !

---

### Post by Nathan 404 on 2007-03-15
I get this error message 
```

Parse error on line 167 of section ServerFlags in file /etc/X11/xorg.conf
        "*" is not a valid keyword in this section.

```

when running the command 
```

sudo aticonfig --initial

```

Any help would be great. I am a complete newb so please don't assume I know anything.

---

### Post by castoroil97 on 2007-03-16
After working 3 weeks on my video card, I downloaded envy and *FINALLY* got it working!!!

My ATI card was a 200m mobility express for a toshiba laptop

Thanks Ubuntu community and especially the creator of envy!!!

Get Envy from here

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by FAT_C on 2007-03-25
> **mr.f said:**
> I ran into the same problem, and it turned out the reason was that the default shell in edgy is dash, not bash like in previous Ubuntu versions. dash is a light-weight shell but does not have all the features of bash.

So, the solution is to replace the  /usr/bin/sh from a symlink to dash to a symlink to bash, start a new shell, and retry the installer script.

Also, I found a more up-to-date ATI driver install howto for Edgy here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

can you tell me how to "replace the  /usr/bin/sh from a symlink to dash to a symlink to bash"??

i got the same problem too

---

### Post by Pett on 2007-03-28
> **castoroil97 said:**
> After working 3 weeks on my video card, I downloaded envy and *FINALLY* got it working!!!

My ATI card was a 200m mobility express for a toshiba laptop

Thanks Ubuntu community and especially the creator of envy!!!

Get Envy from here

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

MAN THANK YOU!!! Three days without sleeping and finally it's working!
I wish I had found this three days ago, I could have slept more than two hours a day :-)
I have ATI mobility radeon x1300 on my dell laptop. Thanks again!

---

### Post by The Afterdark on 2007-06-22
My initial problem: I installed fglrx drivers through the following method:

sudo apt-get install xorg-driver-fglrx fglrx-control

then I edited the xorg.conf file to change the Driver to "fglrx".
I saved it, restarted the system.  Apparently, My system's graphics seem to have downgraded or something.  Desktop Effects don't work anymore, and when I type fgl_glxgears at the terminal, it doesn't give me the gears like it's supposed to.

Then I tried the method in this post, and I came up with the same exact error here:

> **dracomordag said:**
> david@desktop:~$ ./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.27.10......................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 156: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
david@desktop:~$


So then I tried this wiki here, that didnt work either, and gave me the same error, if I tried the second method.

> **mr.f said:**
> I ran into the same problem, and it turned out the reason was that the default shell in edgy is dash, not bash like in previous Ubuntu versions. dash is a light-weight shell but does not have all the features of bash.

So, the solution is to replace the  /usr/bin/sh from a symlink to dash to a symlink to bash, start a new shell, and retry the installer script.

Also, I found a more up-to-date ATI driver install howto for Edgy here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Help anyone?  Please?  I'm using ATI X800 Pro, on Ubuntu 7.04.

---

### Post by mcraig on 2007-06-29
I could be totally wrong but that shouldn't be too hard to fix, go into the restricted drivers and check or uncheck it whatever its set to, reboot, then do it again till its checked, it should basically re-install the restricted driver overwriting whatever you have installed and you should be good to go.

Another thing to try would be go to etc/X11 and rename your xorg.conf something like backup-xorg.conf and reboot, it should act as if you haven't configured X and create you a new hopefully working config, if not just go back to that folder and rename backup-xorg.conf to xorg.conf and you'll have to try something else.

Hope that helps

---

### Post by Maff88 on 2007-07-10
Hi

Im very new to ubuntu so bare with me.

I have an Asus w3j laptop

I have downlaoded the "ati-driver-installer-8-26-17-x86.run" from the link . I then did the installing of "necessary tools"

But when i do the next bit "creat .deb packages" i get ths problem...

```
chmod: unrecognised option '--buildpkg'
```

Now im not to sure what they means or what i need to do to get it to work so i was hopeing someone would be able to help me out

Thanks

---

### Post by Auax on 2007-07-21
Why do I get this? ```
dpkg: error processing xorg-driver-fglrx_8.26.18-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.26.18-1_i386.deb

```

---

### Post by AR_Kozz on 2007-08-09
dan@dan-desktop:~/Desktop$ ./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.26.18..................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 163: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

Anyone else have this happen? It happened with the newer version too, and still happens if I leave off the buildpkg arguments. So it's not a corrupted download.

What could be producing a syntax error in the installer?

---

### Post by chaitm on 2007-08-09
Hi,

I had enabled the ATI drivers hoping I could get Desktop effects to work; the only improvement was that my screen stopped whiting out, but still displayed an error message, and Desktop Effects remain disabled.

When I disabled the ATI driver, hoping the system would switch back to normal, XServer didnt work, I had only a terminal interface to Ubuntu, and I reinstalled the system.

What should I do to disable the ATI drivers without losing my GUI?

I have an ATI Radeon XPress 1100 card(on chip graphics) on my laptop.

Is it not possible to use Desktop Effects? 

I run the x86 version of Ubuntu on an AMD64 dual core, I don't run the 64 bit version because most sofware is written for the 32 bit version.

Thanks!

---

### Post by Jipatsu on 2007-09-25
Hey there,

this is a great guide for making ATI gfx card working.
but I seem to have problems in the point I need to install the kernel moduels with cmd:
[B]
sudo module-assistant build,install fglrx[/B]

I get:

dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
		cat /usr/src/modules/fglrx/debian/control.template > /usr/src/modules/fglrx/debian/control; \
	fi
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \
		mv /usr/src/modules/fglrx/debian/postinst /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.20-16-generic.postinst; \
	fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Siirrytään hakemistoon "/usr/src/linux-headers-2.6.20-16-generic"
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
[B]/usr/src/modules/fglrx/firegl_public.c:180: error: expected declaration specifiers or ‘...’ before ‘mlock’
/usr/src/modules/fglrx/firegl_public.c:180: error: expected declaration specifiers or ‘...’ before ‘addr’
/usr/src/modules/fglrx/firegl_public.c:180: error: expected declaration specifiers or ‘...’ before ‘len’
/usr/src/modules/fglrx/firegl_public.c:182: warning: return type defaults to ‘int’
/usr/src/modules/fglrx/firegl_public.c: In function ‘_syscall2’:
/usr/src/modules/fglrx/firegl_public.c:182: error: expected declaration specifiers before ‘_syscall2’
/usr/src/modules/fglrx/firegl_public.c:215: error: parameter ‘__ke_debuglevel’ is initialized
/usr/src/modules/fglrx/firegl_public.c:216: error: parameter ‘__ke_moduleflags’ is initialized
/usr/src/modules/fglrx/firegl_public.c:219: error: storage class specified for parameter ‘__mod_author219’
/usr/src/modules/fglrx/firegl_public.c:219: error: parameter ‘__mod_author219’ is initialized
/usr/src/modules/fglrx/firegl_public.c:219: warning: ‘__used__’ attribute ignored
/usr/src/modules/fglrx/firegl_public.c:219: error: section attribute not allowed for ‘__mod_author219’
/usr/src/modules/fglrx/firegl_public.c:220: error: storage class specified for parameter ‘__mod_description220’
/usr/src/modules/fglrx/firegl_public.c:220: error: parameter ‘__mod_description220’ is initialized
/usr/src/modules/fglrx/firegl_public.c:220: warning: ‘__used__’ attribute ignored
/usr/src/modules/fglrx/firegl_public.c:220: error: section attribute not allowed for ‘__mod_description220’
/usr/src/modules/fglrx/firegl_public.c:224: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:224: error: expected declaration specifiers before ‘;’ token
/usr/src/modules/fglrx/firegl_public.c:224: error: storage class specified for parameter ‘__param_perm_check_firegl’
/usr/src/modules/fglrx/firegl_public.c:224: error: parameter ‘__param_perm_check_firegl’ is initialized
/usr/src/modules/fglrx/firegl_public.c:224: error: storage class specified for parameter ‘__param_str_firegl’
/usr/src/modules/fglrx/firegl_public.c:224: error: parameter ‘__param_str_firegl’ is initialized
/usr/src/modules/fglrx/firegl_public.c:224: error: storage class specified for parameter ‘__param_firegl’
/usr/src/modules/fglrx/firegl_public.c:224: error: parameter ‘__param_firegl’ is initialized
/usr/src/modules/fglrx/firegl_public.c:224: warning: ‘__used__’ attribute ignored
/usr/src/modules/fglrx/firegl_public.c:224: error: section attribute not allowed for ‘__param_firegl’
/usr/src/modules/fglrx/firegl_public.c:224: error: alignment may not be specified for ‘__param_firegl’
/usr/src/modules/fglrx/firegl_public.c:224: error: ‘firegl’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:224: error: (Each undeclared identifier is reported only once
/usr/src/modules/fglrx/firegl_public.c:224: error: for each function it appears in.)
/usr/src/modules/fglrx/firegl_public.c:224: error: storage class specified for parameter ‘__mod_firegltype224’
/usr/src/modules/fglrx/firegl_public.c:224: error: parameter ‘__mod_firegltype224’ is initialized
/usr/src/modules/fglrx/firegl_public.c:224: warning: ‘__used__’ attribute ignored
/usr/src/modules/fglrx/firegl_public.c:224: error: section attribute not allowed for ‘__mod_firegltype224’
/usr/src/modules/fglrx/firegl_public.c:227: error: storage class specified for parameter ‘__mod_license227’
/usr/src/modules/fglrx/firegl_public.c:227: error: parameter ‘__mod_license227’ is initialized
/usr/src/modules/fglrx/firegl_public.c:227: warning: ‘__used__’ attribute ignored
/usr/src/modules/fglrx/firegl_public.c:227: error: section attribute not allowed for ‘__mod_license227’
/usr/src/modules/fglrx/firegl_public.c:233: error: parameter ‘__ke_UTS_RELEASE’ is initialized
/usr/src/modules/fglrx/firegl_public.c:233: error: ‘UTS_RELEASE’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:234: error: parameter ‘__ke_PAGE_SHIFT’ is initialized
/usr/src/modules/fglrx/firegl_public.c:235: error: parameter ‘__ke_PAGE_SIZE’ is initialized
/usr/src/modules/fglrx/firegl_public.c:236: error: parameter ‘__ke_PAGE_MASK’ is initialized
/usr/src/modules/fglrx/firegl_public.c:237: error: parameter ‘__ke_LINUX_VERSION_CODE’ is initialized
/usr/src/modules/fglrx/firegl_public.c:244: error: parameter ‘__ke_MODVERSIONS_State’ is initialized
/usr/src/modules/fglrx/firegl_public.c:252: error: parameter ‘__ke_SMP_State’ is initialized
/usr/src/modules/fglrx/firegl_public.c:260: error: parameter ‘__ke_PAE_State’ is initialized
/usr/src/modules/fglrx/firegl_public.c:269: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:271: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:273: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:275: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:279: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:282: error: storage class specified for parameter ‘firegl_fops’
/usr/src/modules/fglrx/firegl_public.c:282: error: parameter ‘firegl_fops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:287: error: ‘ip_firegl_open’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:288: error: ‘ip_firegl_release’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:289: error: ‘ip_firegl_ioctl’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:290: error: ‘ip_firegl_mmap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:293: error: ‘ip_firegl_compat_ioctl’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:305: error: storage class specified for parameter ‘device_t’
/usr/src/modules/fglrx/firegl_public.c:307: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘firegl_public_device’
In file included from /usr/src/modules/fglrx/firegl_public.c:313:
/usr/src/modules/fglrx/drm.h:104: error: storage class specified for parameter ‘drm_handle_t’
/usr/src/modules/fglrx/drm.h:105: error: storage class specified for parameter ‘drm_context_t’
/usr/src/modules/fglrx/drm.h:106: error: storage class specified for parameter ‘drm_drawable_t’
/usr/src/modules/fglrx/drm.h:107: error: storage class specified for parameter ‘drm_magic_t’
/usr/src/modules/fglrx/drm.h:124: error: storage class specified for parameter ‘drm_clip_rect_t’
/usr/src/modules/fglrx/drm.h:136: error: storage class specified for parameter ‘drm_tex_region_t’
/usr/src/modules/fglrx/drm.h:148: error: storage class specified for parameter ‘drm_hw_lock_t’
/usr/src/modules/fglrx/drm.h:182: error: storage class specified for parameter ‘drm_version_t’
/usr/src/modules/fglrx/drm.h:193: error: storage class specified for parameter ‘drm_unique_t’
/usr/src/modules/fglrx/drm.h:199: error: expected specifier-qualifier-list before ‘drm_version_t’
/usr/src/modules/fglrx/drm.h:200: error: storage class specified for parameter ‘drm_list_t’
/usr/src/modules/fglrx/drm.h:205: error: storage class specified for parameter ‘drm_block_t’
/usr/src/modules/fglrx/drm.h:221: error: storage class specified for parameter ‘drm_control_t’
/usr/src/modules/fglrx/drm.h:233: error: storage class specified for parameter ‘drm_map_type_t’
/usr/src/modules/fglrx/drm.h:247: error: storage class specified for parameter ‘drm_map_flags_t’
/usr/src/modules/fglrx/drm.h:253: error: storage class specified for parameter ‘drm_ctx_priv_map_t’
/usr/src/modules/fglrx/drm.h:265: error: expected specifier-qualifier-list before ‘drm_map_type_t’
/usr/src/modules/fglrx/drm.h:271: error: storage class specified for parameter ‘drm_map_t’
/usr/src/modules/fglrx/drm.h:284: error: storage class specified for parameter ‘drm_client_t’
/usr/src/modules/fglrx/drm.h:306: error: storage class specified for parameter ‘drm_stat_type_t’
/usr/src/modules/fglrx/drm.h:316: error: expected specifier-qualifier-list before ‘drm_stat_type_t’
/usr/src/modules/fglrx/drm.h:318: error: storage class specified for parameter ‘drm_stats_t’
/usr/src/modules/fglrx/drm.h:334: error: storage class specified for parameter ‘drm_lock_flags_t’
/usr/src/modules/fglrx/drm.h:344: error: expected specifier-qualifier-list before ‘drm_lock_flags_t’
/usr/src/modules/fglrx/drm.h:345: error: storage class specified for parameter ‘drm_lock_t’
/usr/src/modules/fglrx/drm.h:375: error: storage class specified for parameter ‘drm_dma_flags_t’
/usr/src/modules/fglrx/drm.h:397: error: storage class specified for parameter ‘drm_buf_desc_t’
/usr/src/modules/fglrx/drm.h:405: error: expected specifier-qualifier-list before ‘drm_buf_desc_t’
/usr/src/modules/fglrx/drm.h:406: error: storage class specified for parameter ‘drm_buf_info_t’
/usr/src/modules/fglrx/drm.h:415: error: storage class specified for parameter ‘drm_buf_free_t’
/usr/src/modules/fglrx/drm.h:428: error: storage class specified for parameter ‘drm_buf_pub_t’
/usr/src/modules/fglrx/drm.h:437: error: expected specifier-qualifier-list before ‘drm_buf_pub_t’
/usr/src/modules/fglrx/drm.h:438: error: storage class specified for parameter ‘drm_buf_map_t’
/usr/src/modules/fglrx/drm.h:453: error: expected specifier-qualifier-list before ‘drm_dma_flags_t’
/usr/src/modules/fglrx/drm.h:459: error: storage class specified for parameter ‘drm_dma_t’
/usr/src/modules/fglrx/drm.h:465: error: storage class specified for parameter ‘drm_ctx_flags_t’
/usr/src/modules/fglrx/drm.h:474: error: expected specifier-qualifier-list before ‘drm_context_t’
/usr/src/modules/fglrx/drm.h:476: error: storage class specified for parameter ‘drm_ctx_t’
/usr/src/modules/fglrx/drm.h:484: error: expected specifier-qualifier-list before ‘drm_ctx_t’
/usr/src/modules/fglrx/drm.h:485: error: storage class specified for parameter ‘drm_ctx_res_t’
/usr/src/modules/fglrx/drm.h:492: error: expected specifier-qualifier-list before ‘drm_drawable_t’
/usr/src/modules/fglrx/drm.h:493: error: storage class specified for parameter ‘drm_draw_t’
/usr/src/modules/fglrx/drm.h:500: error: expected specifier-qualifier-list before ‘drm_magic_t’
/usr/src/modules/fglrx/drm.h:501: error: storage class specified for parameter ‘drm_auth_t’
/usr/src/modules/fglrx/drm.h:514: error: storage class specified for parameter ‘drm_irq_busid_t’
/usr/src/modules/fglrx/drm.h:521: error: storage class specified for parameter ‘drm_vblank_seq_type_t’
/usr/src/modules/fglrx/drm.h:528: error: expected specifier-qualifier-list before ‘drm_vblank_seq_type_t’
/usr/src/modules/fglrx/drm.h:531: warning: empty declaration
/usr/src/modules/fglrx/drm.h:535: error: expected specifier-qualifier-list before ‘drm_vblank_seq_type_t’
/usr/src/modules/fglrx/drm.h:539: warning: empty declaration
/usr/src/modules/fglrx/drm.h:550: error: storage class specified for parameter ‘drm_wait_vblank_t’
/usr/src/modules/fglrx/drm.h:560: error: storage class specified for parameter ‘drm_agp_mode_t’
/usr/src/modules/fglrx/drm.h:573: error: storage class specified for parameter ‘drm_agp_buffer_t’
/usr/src/modules/fglrx/drm.h:584: error: storage class specified for parameter ‘drm_agp_binding_t’
/usr/src/modules/fglrx/drm.h:606: error: storage class specified for parameter ‘drm_agp_info_t’
/usr/src/modules/fglrx/drm.h:615: error: storage class specified for parameter ‘drm_scatter_gather_t’
/usr/src/modules/fglrx/drm.h:625: error: storage class specified for parameter ‘drm_set_version_t’
/usr/src/modules/fglrx/firegl_public.c:319: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from include/linux/poll.h:4,
                 from /usr/src/modules/fglrx/drmP.h:82,
                 from /usr/src/modules/fglrx/drm_proc.h:41,
                 from /usr/src/modules/fglrx/firegl_public.c:329:
include/asm/poll.h:25: warning: empty declaration
In file included from /usr/src/modules/fglrx/drmP.h:82,
                 from /usr/src/modules/fglrx/drm_proc.h:41,
                 from /usr/src/modules/fglrx/firegl_public.c:329:
include/linux/poll.h:24: warning: empty declaration
include/linux/poll.h:29: error: storage class specified for parameter ‘poll_queue_proc’
include/linux/poll.h:32: error: expected specifier-qualifier-list before ‘poll_queue_proc’
include/linux/poll.h:33: error: storage class specified for parameter ‘poll_table’
include/linux/poll.h:35: error: expected declaration specifiers or ‘...’ before ‘poll_table’
include/linux/poll.h:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/linux/poll.h:41: error: expected ‘)’ before ‘*’ token
include/linux/poll.h:50: warning: empty declaration
include/linux/poll.h:56: error: expected specifier-qualifier-list before ‘poll_table’
include/linux/poll.h:61: warning: empty declaration
include/linux/poll.h:63: error: storage class specified for parameter ‘poll_initwait’
include/linux/poll.h:64: error: storage class specified for parameter ‘poll_freewait’
include/linux/poll.h:73: error: storage class specified for parameter ‘fd_set_bits’
include/linux/poll.h:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/linux/poll.h:101: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/linux/poll.h:109: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/linux/poll.h:115: error: expected declaration specifiers or ‘...’ before ‘fd_set_bits’
include/linux/poll.h:115: error: storage class specified for parameter ‘do_select’
include/linux/poll.h:117: error: storage class specified for parameter ‘do_sys_poll’
In file included from /usr/src/modules/fglrx/drmP.h:83,
                 from /usr/src/modules/fglrx/drm_proc.h:41,
                 from /usr/src/modules/fglrx/firegl_public.c:329:
include/asm/pgalloc.h:17: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:27: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:33: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:62: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:75: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:95: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:107: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:118: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
include/asm/pgalloc.h:124: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from /usr/src/modules/fglrx/drm_proc.h:41,
                 from /usr/src/modules/fglrx/firegl_public.c:329:
/usr/src/modules/fglrx/drmP.h:324: error: storage class specified for parameter ‘drm_ioctl_t’
/usr/src/modules/fglrx/drmP.h:327: error: expected specifier-qualifier-list before ‘drm_ioctl_t’
/usr/src/modules/fglrx/drmP.h:330: error: storage class specified for parameter ‘drm_ioctl_desc_t’
/usr/src/modules/fglrx/drmP.h:334: error: storage class specified for parameter ‘drm_devstate_t’
/usr/src/modules/fglrx/drmP.h:337: error: expected specifier-qualifier-list before ‘drm_magic_t’
/usr/src/modules/fglrx/drmP.h:340: error: storage class specified for parameter ‘drm_magic_entry_t’
/usr/src/modules/fglrx/drmP.h:345: error: storage class specified for parameter ‘drm_magic_head_t’
/usr/src/modules/fglrx/drmP.h:351: error: storage class specified for parameter ‘drm_vma_entry_t’
/usr/src/modules/fglrx/drmP.h:382: error: storage class specified for parameter ‘drm_buf_t’
/usr/src/modules/fglrx/drmP.h:388: error: expected specifier-qualifier-list before ‘drm_buf_t’
/usr/src/modules/fglrx/drmP.h:394: error: storage class specified for parameter ‘drm_waitlist_t’
/usr/src/modules/fglrx/drmP.h:399: error: expected specifier-qualifier-list before ‘drm_buf_t’
/usr/src/modules/fglrx/drmP.h:406: error: storage class specified for parameter ‘drm_freelist_t’
/usr/src/modules/fglrx/drmP.h:414: error: expected specifier-qualifier-list before ‘drm_buf_t’
/usr/src/modules/fglrx/drmP.h:420: error: storage class specified for parameter ‘drm_buf_entry_t’
/usr/src/modules/fglrx/drmP.h:428: error: expected specifier-qualifier-list before ‘drm_magic_t’
/usr/src/modules/fglrx/drmP.h:438: error: storage class specified for parameter ‘drm_file_t’
/usr/src/modules/fglrx/drmP.h:454: error: expected specifier-qualifier-list before ‘drm_ctx_flags_t’
/usr/src/modules/fglrx/drmP.h:457: error: storage class specified for parameter ‘drm_queue_t’
/usr/src/modules/fglrx/drmP.h:463: error: expected specifier-qualifier-list before ‘drm_hw_lock_t’
/usr/src/modules/fglrx/drmP.h:467: error: storage class specified for parameter ‘drm_lock_data_t’
/usr/src/modules/fglrx/drmP.h:474: error: expected specifier-qualifier-list before ‘drm_buf_entry_t’
/usr/src/modules/fglrx/drmP.h:493: error: storage class specified for parameter ‘drm_device_dma_t’
/usr/src/modules/fglrx/drmP.h:535: error: storage class specified for parameter ‘drm_sg_mem_t’
/usr/src/modules/fglrx/drmP.h:539: error: expected specifier-qualifier-list before ‘drm_hw_lock_t’
/usr/src/modules/fglrx/drmP.h:540: error: storage class specified for parameter ‘drm_sigdata_t’
/usr/src/modules/fglrx/drmP.h:547: error: expected specifier-qualifier-list before ‘drm_map_t’
/usr/src/modules/fglrx/drmP.h:548: error: storage class specified for parameter ‘drm_map_list_t’
/usr/src/modules/fglrx/drmP.h:550: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_local_map_t’
/usr/src/modules/fglrx/drmP.h:557: error: expected specifier-qualifier-list before ‘drm_context_t’
/usr/src/modules/fglrx/drmP.h:559: error: storage class specified for parameter ‘drm_ctx_list_t’
/usr/src/modules/fglrx/drmP.h:594: error: expected specifier-qualifier-list before ‘drm_stat_type_t’
/usr/src/modules/fglrx/drmP.h:684: error: storage class specified for parameter ‘drm_device_t’
/usr/src/modules/fglrx/drmP.h:692: error: storage class specified for parameter ‘FGLDRM_flags’
/usr/src/modules/fglrx/drmP.h:693: error: storage class specified for parameter ‘FGLDRM_parse_options’
/usr/src/modules/fglrx/drmP.h:694: error: storage class specified for parameter ‘FGLDRM_cpu_valid’
/usr/src/modules/fglrx/drmP.h:698: error: storage class specified for parameter ‘FGLDRM_version’
/usr/src/modules/fglrx/drmP.h:699: error: storage class specified for parameter ‘FGLDRM_open’
/usr/src/modules/fglrx/drmP.h:700: error: storage class specified for parameter ‘FGLDRM_release’
/usr/src/modules/fglrx/drmP.h:702: error: storage class specified for parameter ‘FGLDRM_ioctl’
/usr/src/modules/fglrx/drmP.h:704: error: storage class specified for parameter ‘FGLDRM_lock’
/usr/src/modules/fglrx/drmP.h:706: error: storage class specified for parameter ‘FGLDRM_unlock’
/usr/src/modules/fglrx/drmP.h:707: error: storage class specified for parameter ‘FGLDRM_fb_loaded’
/usr/src/modules/fglrx/drmP.h:711: error: expected declaration specifiers or ‘...’ before ‘drm_device_t’
/usr/src/modules/fglrx/drmP.h:711: error: storage class specified for parameter ‘FGLDRM_open_helper’
/usr/src/modules/fglrx/drmP.h:712: error: storage class specified for parameter ‘FGLDRM_flush’
/usr/src/modules/fglrx/drmP.h:713: error: storage class specified for parameter ‘FGLDRM_fasync’
/usr/src/modules/fglrx/drmP.h:716: error: storage class specified for parameter ‘FGLDRM_vm_open’
/usr/src/modules/fglrx/drmP.h:717: error: storage class specified for parameter ‘FGLDRM_vm_close’
/usr/src/modules/fglrx/drmP.h:718: error: storage class specified for parameter ‘FGLDRM_vm_shm_close’
/usr/src/modules/fglrx/drmP.h:720: error: storage class specified for parameter ‘FGLDRM_mmap_dma’
/usr/src/modules/fglrx/drmP.h:721: error: storage class specified for parameter ‘FGLDRM_mmap’
/usr/src/modules/fglrx/drmP.h:722: error: storage class specified for parameter ‘FGLDRM_poll’
/usr/src/modules/fglrx/drmP.h:723: error: storage class specified for parameter ‘FGLDRM_read’
/usr/src/modules/fglrx/drmP.h:726: error: storage class specified for parameter ‘FGLDRM_mem_init’
/usr/src/modules/fglrx/drmP.h:728: error: storage class specified for parameter ‘FGLDRM_mem_info’
/usr/src/modules/fglrx/drmP.h:729: error: storage class specified for parameter ‘FGLDRM_alloc’
/usr/src/modules/fglrx/drmP.h:730: error: storage class specified for parameter ‘FGLDRM_calloc’
/usr/src/modules/fglrx/drmP.h:732: error: storage class specified for parameter ‘FGLDRM_realloc’
/usr/src/modules/fglrx/drmP.h:733: error: storage class specified for parameter ‘FGLDRM_free’
/usr/src/modules/fglrx/drmP.h:734: error: storage class specified for parameter ‘FGLDRM_alloc_pages’
/usr/src/modules/fglrx/drmP.h:736: error: storage class specified for parameter ‘FGLDRM_free_pages’
/usr/src/modules/fglrx/drmP.h:737: error: expected declaration specifiers or ‘...’ before ‘drm_device_t’
/usr/src/modules/fglrx/drmP.h:737: error: storage class specified for parameter ‘FGLDRM_ioremap’
/usr/src/modules/fglrx/drmP.h:739: error: expected declaration specifiers or ‘...’ before ‘drm_device_t’
/usr/src/modules/fglrx/drmP.h:739: error: storage class specified for parameter ‘FGLDRM_ioremap_nocache’
/usr/src/modules/fglrx/drmP.h:740: error: expected declaration specifiers or ‘...’ before ‘drm_device_t’
/usr/src/modules/fglrx/drmP.h:740: error: storage class specified for parameter ‘FGLDRM_ioremapfree’
/usr/src/modules/fglrx/drmP.h:751: error: storage class specified for parameter ‘FGLDRM_irq_by_busid’
/usr/src/modules/fglrx/drmP.h:753: error: storage class specified for parameter ‘FGLDRM_getunique’
/usr/src/modules/fglrx/drmP.h:755: error: storage class specified for parameter ‘FGLDRM_setunique’
/usr/src/modules/fglrx/drmP.h:757: error: storage class specified for parameter ‘FGLDRM_getmap’
/usr/src/modules/fglrx/drmP.h:759: error: storage class specified for parameter ‘FGLDRM_getclient’
/usr/src/modules/fglrx/drmP.h:761: error: storage class specified for parameter ‘FGLDRM_getstats’
/usr/src/modules/fglrx/drmP.h:763: error: storage class specified for parameter ‘FGLDRM_setversion’
/usr/src/modules/fglrx/drmP.h:767: error: storage class specified for parameter ‘FGLDRM_resctx’
/usr/src/modules/fglrx/drmP.h:769: error: storage class specified for parameter ‘FGLDRM_addctx’
/usr/src/modules/fglrx/drmP.h:771: error: storage class specified for parameter ‘FGLDRM_modctx’
/usr/src/modules/fglrx/drmP.h:773: error: storage class specified for parameter ‘FGLDRM_getctx’
/usr/src/modules/fglrx/drmP.h:775: error: storage class specified for parameter ‘FGLDRM_switchctx’
/usr/src/modules/fglrx/drmP.h:777: error: storage class specified for parameter ‘FGLDRM_newctx’
/usr/src/modules/fglrx/drmP.h:779: error: storage class specified for parameter ‘FGLDRM_rmctx’
/usr/src/modules/fglrx/drmP.h:781: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/drmP.h:782: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/drmP.h:790: error: storage class specified for parameter ‘FGLDRM_setsareactx’
/usr/src/modules/fglrx/drmP.h:792: error: storage class specified for parameter ‘FGLDRM_getsareactx’
/usr/src/modules/fglrx/drmP.h:796: error: storage class specified for parameter ‘FGLDRM_adddraw’
/usr/src/modules/fglrx/drmP.h:798: error: storage class specified for parameter ‘FGLDRM_rmdraw’
/usr/src/modules/fglrx/drmP.h:802: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/drmP.h:804: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/drmP.h:806: error: storage class specified for parameter ‘FGLDRM_getmagic’
/usr/src/modules/fglrx/drmP.h:808: error: storage class specified for parameter ‘FGLDRM_authmagic’
/usr/src/modules/fglrx/drmP.h:812: error: storage class specified for parameter ‘FGLDRM_noop’
/usr/src/modules/fglrx/drmP.h:816: error: storage class specified for parameter ‘FGLDRM_lock_take’
/usr/src/modules/fglrx/drmP.h:817: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/drmP.h:820: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/drmP.h:823: error: storage class specified for parameter ‘FGLDRM_notifier’
/usr/src/modules/fglrx/drmP.h:826: error: storage class specified for parameter ‘FGLDRM_order’
/usr/src/modules/fglrx/drmP.h:828: error: storage class specified for parameter ‘FGLDRM_addmap’
/usr/src/modules/fglrx/drmP.h:830: error: storage class specified for parameter ‘FGLDRM_rmmap’
/usr/src/modules/fglrx/drmP.h:898: error: expected declaration specifiers or ‘...’ before ‘drm_device_t’
/usr/src/modules/fglrx/drmP.h:902: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/drmP.h:908: error: storage class specified for parameter ‘FGLDRM_proc_cleanup’
/usr/src/modules/fglrx/drmP.h:911: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/drmP.h:914: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/drmP.h:918: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/drmP.h:921: error: expected ‘)’ before ‘*’ token
In file included from /usr/src/modules/fglrx/firegl_public.c:329:
/usr/src/modules/fglrx/drm_proc.h:44: error: storage class specified for parameter ‘FGLDRM_name_info’
/usr/src/modules/fglrx/drm_proc.h:46: error: storage class specified for parameter ‘FGLDRM_vm_info’
/usr/src/modules/fglrx/drm_proc.h:48: error: storage class specified for parameter ‘FGLDRM_clients_info’
/usr/src/modules/fglrx/drm_proc.h:50: error: storage class specified for parameter ‘FGLDRM_queues_info’
/usr/src/modules/fglrx/drm_proc.h:52: error: storage class specified for parameter ‘FGLDRM_bufs_info’
/usr/src/modules/fglrx/drm_proc.h:55: error: storage class specified for parameter ‘FGLDRM_vma_info’
/usr/src/modules/fglrx/drm_proc.h:64: error: parameter ‘FGLDRM_proc_list’ is initialized
/usr/src/modules/fglrx/drm_proc.h:65: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:65: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:65: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:65: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:65: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:66: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:66: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:66: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:66: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:66: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:66: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:66: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:67: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:67: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:67: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:67: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:67: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:67: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:67: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:68: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:68: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:68: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:68: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:68: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:68: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:68: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:69: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:69: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:69: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:69: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:69: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:69: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:69: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:70: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:70: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:70: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:70: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:70: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:70: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:70: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:72: warning: braces around scalar initializer
/usr/src/modules/fglrx/drm_proc.h:72: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:72: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/drm_proc.h:72: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:72: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:72: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/drm_proc.h:72: warning: (near initialization for ‘FGLDRM_proc_list’)
/usr/src/modules/fglrx/drm_proc.h:90: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/drm_proc.h:144: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:174: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:213: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:269: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:292: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:339: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:362: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:409: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:432: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:466: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:480: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/drm_proc.h:537: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:335: error: storage class specified for parameter ‘drm_proclist’
/usr/src/modules/fglrx/firegl_public.c:335: error: parameter ‘drm_proclist’ is initialized
/usr/src/modules/fglrx/firegl_public.c:347: error: storage class specified for parameter ‘firegl_stub_list_t’
/usr/src/modules/fglrx/firegl_public.c:348: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘firegl_stub_list’
/usr/src/modules/fglrx/firegl_public.c:350: error: storage class specified for parameter ‘firegl_stub_root’
/usr/src/modules/fglrx/firegl_public.c:351: error: storage class specified for parameter ‘firegl_minor’
/usr/src/modules/fglrx/firegl_public.c:354: error: expected declaration specifiers or ‘...’ before ‘device_t’
/usr/src/modules/fglrx/firegl_public.c:357: error: storage class specified for parameter ‘firegl_drm_stub_info_t’
/usr/src/modules/fglrx/firegl_public.c:358: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘firegl_stub_info’
/usr/src/modules/fglrx/firegl_public.c:360: error: storage class specified for parameter ‘__ke_pte_phys_addr_str’
/usr/src/modules/fglrx/firegl_public.c:363: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:368: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:379: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:380: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:381: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:382: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:383: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:384: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:385: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:390: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:396: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:404: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:414: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:419: error: expected declaration specifiers or ‘...’ before ‘poll_table’
/usr/src/modules/fglrx/firegl_public.c:420: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:431: error: storage class specified for parameter ‘firegl_interrupt_file_ops’
/usr/src/modules/fglrx/firegl_public.c:431: error: parameter ‘firegl_interrupt_file_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:432: error: ‘firegl_interrupt_open_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:433: error: ‘firegl_interrupt_read_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:434: error: ‘firegl_interrupt_release_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:435: error: ‘firegl_interrupt_poll_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:438: error: parameter ‘firegl_proc_list’ is initialized
/usr/src/modules/fglrx/firegl_public.c:440: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:440: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:440: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:440: error: ‘drm_name_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:440: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:440: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:440: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:440: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:441: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:441: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:441: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:441: error: ‘drm_mem_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:441: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:441: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:441: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:441: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:441: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:441: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:442: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:442: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:442: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:442: error: ‘drm_mem_info1_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:442: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:442: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:442: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:442: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:442: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:442: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:443: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:443: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:443: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:443: error: ‘drm_vm_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:443: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:443: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:443: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:443: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:443: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:443: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:444: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:444: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:444: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:444: error: ‘drm_clients_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:444: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:444: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:444: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:444: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:444: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:444: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:445: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:445: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:445: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:445: error: ‘firegl_lock_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:445: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:445: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:445: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:445: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:445: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:445: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:446: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:446: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:446: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:446: error: ‘firegl_umm_info_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:446: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:446: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:446: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:446: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:446: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:446: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:451: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:451: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:451: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:451: error: ‘firegl_bios_version_wrap’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:451: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:451: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:451: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:451: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:451: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:451: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:452: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:452: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:452: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:452: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:452: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:452: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:452: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:452: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:452: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:453: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:453: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:453: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:453: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:453: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:453: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:453: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:453: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:453: warning: (near initialization for ‘firegl_proc_list’)
/usr/src/modules/fglrx/firegl_public.c:456: error: expected ‘)’ before ‘*’ token
/usr/src/modules/fglrx/firegl_public.c:521: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:545: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:569: error: storage class specified for parameter ‘firegl_stub_fops’
/usr/src/modules/fglrx/firegl_public.c:569: error: parameter ‘firegl_stub_fops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:571: error: ‘firegl_stub_open’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:574: error: expected declaration specifiers or ‘...’ before ‘device_t’
/usr/src/modules/fglrx/firegl_public.c:575: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:594: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:611: error: expected declaration specifiers or ‘...’ before ‘device_t’
/usr/src/modules/fglrx/firegl_public.c:612: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:646: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:655: error: storage class specified for parameter ‘fglrx_pci_table’
/usr/src/modules/fglrx/firegl_public.c:655: error: parameter ‘fglrx_pci_table’ is initialized
/usr/src/modules/fglrx/firegl_public.c:657: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:657: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:658: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:658: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:658: warning: initialization makes pointer from integer without a cast
/usr/src/modules/fglrx/firegl_public.c:659: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:659: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:659: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:659: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:660: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:660: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:660: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:660: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:661: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:661: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:661: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:661: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:662: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:662: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:662: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:662: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:663: error: field name not in record or union initializer
/usr/src/modules/fglrx/firegl_public.c:663: error: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:663: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:663: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:665: warning: braces around scalar initializer
/usr/src/modules/fglrx/firegl_public.c:665: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:665: warning: excess elements in scalar initializer
/usr/src/modules/fglrx/firegl_public.c:665: warning: (near initialization for ‘fglrx_pci_table’)
/usr/src/modules/fglrx/firegl_public.c:669: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:683: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:717: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:751: error: storage class specified for parameter ‘fglrx_pci_driver’
/usr/src/modules/fglrx/firegl_public.c:751: error: parameter ‘fglrx_pci_driver’ is initialized
/usr/src/modules/fglrx/firegl_public.c:755: error: ‘fglrx_pci_probe’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:757: error: ‘fglrx_pci_suspend’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:758: error: ‘fglrx_pci_resume’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:767: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:856: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:886: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:886: error: ‘init_module’ defined both normally and as an alias
/usr/src/modules/fglrx/firegl_public.c:886: error: expected declaration specifiers before ‘;’ token
/usr/src/modules/fglrx/firegl_public.c:887: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:887: error: ‘cleanup_module’ defined both normally and as an alias
/usr/src/modules/fglrx/firegl_public.c:887: error: expected declaration specifiers before ‘;’ token
/usr/src/modules/fglrx/firegl_public.c:893: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:906: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:912: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:920: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:926: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:931: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:955: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:962: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:967: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:972: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:978: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:984: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:990: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:995: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1000: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1005: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1015: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1020: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1025: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1066: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1078: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1083: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1090: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1101: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1106: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1115: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1120: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1125: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1130: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1135: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1147: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1152: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1159: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1164: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1205: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1213: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1218: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1223: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1228: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1234: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1240: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1249: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1285: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1293: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1301: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1309: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1317: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1323: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1329: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1335: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1345: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1354: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1365: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1370: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1375: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1380: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1385: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1390: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1397: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1402: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1407: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1412: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1417: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1422: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1429: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1434: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1439: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1444: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1454: error: storage class specified for parameter ‘PFNMLOCK’
/usr/src/modules/fglrx/firegl_public.c:1455: error: storage class specified for parameter ‘PFNMUNLOCK’
/usr/src/modules/fglrx/firegl_public.c:1459: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1474: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1489: error: storage class specified for parameter ‘PFNMODIFYLDT’
/usr/src/modules/fglrx/firegl_public.c:1492: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1513: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1518: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1525: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1634: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1650: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1666: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1671: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1676: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1690: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1701: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1706: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1711: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1720: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1732: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1752: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1763: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1768: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1773: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1778: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1783: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1788: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1792: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1796: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1801: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1806: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1811: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1816: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1821: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1826: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1831: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1836: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1841: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1851: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1873: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1887: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1896: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1905: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1911: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1917: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1929: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1934: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1939: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1944: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1949: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1954: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1959: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1964: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:1984: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2016: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2031: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2136: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2141: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2146: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2151: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2156: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2161: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2166: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2177: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2190: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2195: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2205: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2210: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2215: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2245: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2281: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2290: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2299: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2308: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2318: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2327: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2335: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2340: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2345: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2350: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2355: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2360: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2365: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2370: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2376: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2381: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2386: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2391: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2399: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2404: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2409: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2414: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2419: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2424: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2429: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2437: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2442: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2461: error: storage class specified for parameter ‘irq_handler_func’
/usr/src/modules/fglrx/firegl_public.c:2464: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2472: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2480: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2488: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2497: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2508: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2514: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2531: error: storage class specified for parameter ‘mem_map_t’
/usr/src/modules/fglrx/firegl_public.c:2532: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/src/modules/fglrx/firegl_public.c:2537: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_vm_nopage’
/usr/src/modules/fglrx/firegl_public.c:2573: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_vm_shm_nopage’
/usr/src/modules/fglrx/firegl_public.c:2659: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_vm_dma_nopage’
/usr/src/modules/fglrx/firegl_public.c:2699: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_vm_kmap_nopage’
/usr/src/modules/fglrx/firegl_public.c:2737: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_vm_pcie_nopage’
/usr/src/modules/fglrx/firegl_public.c:2791: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vm_nopage’
/usr/src/modules/fglrx/firegl_public.c:2828: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vm_shm_nopage’
/usr/src/modules/fglrx/firegl_public.c:2842: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vm_dma_nopage’
/usr/src/modules/fglrx/firegl_public.c:2850: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vm_kmap_nopage’
/usr/src/modules/fglrx/firegl_public.c:2858: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vm_pcie_nopage’
/usr/src/modules/fglrx/firegl_public.c:2938: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2943: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2948: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2953: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2962: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2974: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:2998: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3025: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3041: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3043: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3045: error: storage class specified for parameter ‘vm_ops’
/usr/src/modules/fglrx/firegl_public.c:3045: error: parameter ‘vm_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3047: error: ‘vm_nopage’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3048: error: ‘ip_drm_vm_open’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3049: error: ‘ip_drm_vm_close’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3063: error: storage class specified for parameter ‘vm_shm_ops’
/usr/src/modules/fglrx/firegl_public.c:3063: error: parameter ‘vm_shm_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3065: error: ‘vm_shm_nopage’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3070: error: storage class specified for parameter ‘vm_pci_bq_ops’
/usr/src/modules/fglrx/firegl_public.c:3070: error: parameter ‘vm_pci_bq_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3072: error: ‘vm_dma_nopage’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3077: error: storage class specified for parameter ‘vm_ctx_ops’
/usr/src/modules/fglrx/firegl_public.c:3077: error: parameter ‘vm_ctx_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3084: error: storage class specified for parameter ‘vm_pcie_ops’
/usr/src/modules/fglrx/firegl_public.c:3084: error: parameter ‘vm_pcie_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3086: error: ‘vm_pcie_nopage’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3091: error: storage class specified for parameter ‘vm_kmap_ops’
/usr/src/modules/fglrx/firegl_public.c:3091: error: parameter ‘vm_kmap_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3093: error: ‘vm_kmap_nopage’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3100: error: storage class specified for parameter ‘vm_agp_bq_ops’
/usr/src/modules/fglrx/firegl_public.c:3100: error: parameter ‘vm_agp_bq_ops’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3120: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3297: error: parameter ‘__ke_agp_try_unsupported’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3300: error: storage class specified for parameter ‘__fgl_agp_init’
/usr/src/modules/fglrx/firegl_public.c:3301: error: storage class specified for parameter ‘__fgl_agp_cleanup’
/usr/src/modules/fglrx/firegl_public.c:3302: error: storage class specified for parameter ‘__fgl_agp_try_unsupported’
/usr/src/modules/fglrx/firegl_public.c:3303: error: storage class specified for parameter ‘__fgl_agp_allocate_memory_phys_list’
/usr/src/modules/fglrx/firegl_public.c:3319: error: parameter ‘__ke_firegl_agpgart_inuse’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3335: error: storage class specified for parameter ‘drm_agp_t’
/usr/src/modules/fglrx/firegl_public.c:3346: error: storage class specified for parameter ‘firegl_agp_bridge’
/usr/src/modules/fglrx/firegl_public.c:3346: error: parameter ‘firegl_agp_bridge’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3347: error: storage class specified for parameter ‘firegl_pci_device’
/usr/src/modules/fglrx/firegl_public.c:3347: error: parameter ‘firegl_pci_device’ is initialized
/usr/src/modules/fglrx/firegl_public.c:3351: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3356: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3361: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3367: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3373: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3378: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/usr/src/modules/fglrx/firegl_public.c:3387: error: expected declaration specifiers before ‘;’ token
/usr/src/modules/fglrx/firegl_public.c:3428: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/src/modules/fglrx/firegl_public.c:3537: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3563: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3571: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3596: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3610: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3616: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3624: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3632: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3640: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3649: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3680: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3691: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3697: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3763: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3769: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3840: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3856: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3862: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/modules/fglrx/firegl_public.c:3866: error: old-style parameter declarations in prototyped function definition
/usr/src/modules/fglrx/firegl_public.c:180: error: parameter name omitted
/usr/src/modules/fglrx/firegl_public.c:180: error: parameter name omitted
/usr/src/modules/fglrx/firegl_public.c:180: error: parameter name omitted
/usr/src/modules/fglrx/firegl_public.c:3866: error: expected ‘{’ at end of input
make[2]: *** [/usr/src/modules/fglrx/firegl_public.o] Virhe 1
make[1]: *** [_module_/usr/src/modules/fglrx] Virhe 2
make[1]: Poistutaan hakemistosta "/usr/src/linux-headers-2.6.20-16-generic"
make: *** [build] Virhe 2[/B]

I'm quite new with the linux enviroment and this kind of things makes it harder to get known with the linux.

I'm using Ubuntu v 7.04 and my vid card is ati integrated xpress 200m on laptop.


any suggestions?

---

### Post by cdcweb on 2008-02-07
> **fitzman49 said:**
> Finally ATI released the much anticipated update to the fglrx driver which now has support for xorg 7.0 and works with all xseries cards.  Mine (xpress 200m) did not work with the fglrx 8.25.18 drivers but now have full support and 3D acceleration.  These drivers also address the black screen hanging issue when xorg is shutdown or restarted.  Heres a quick tutorial on how I got it working.  Much thanks to IVHassel for the tutoiral before that I used to get the old drivers working.:) 

Cards that are known to work with these new drivers can be found here: [https://www2.ati.com/drivers/linux/linux_8.26.18.html]("https://www2.ati.com/drivers/linux/linux_8.26.18.html")


Installing the new driver

Download the ATI driver installer from the ATI Website: 32bit Installer:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run]("https://www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run")

**Edit:**64 bit users:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run]("https://www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run")

**Edit:**New 8.27.10 drivers are now available.  Follow the guide but change the file names accordingly.

32 Bit: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run]("https://www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run")

64 Bit:[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.27.10-x86_64.run]("https://www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.27.10-x86_64.run")

This guide refers to the 32bit version of the driver. If you are using a x86_64 System you need the 64bit Installer. The installation procedure should be the same as for 32bit, except some filenames will differ slightly.

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

Install necessary tools:
```
sudo apt-get update 
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```



Create .deb packages:

```
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
```
/
At this point  I get this;

```

user@user-laptop:~$ chmod +x ati-driver-installer-8.27.10-x86.run

user@user-laptop:~$ ./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/dapper

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.27.10
....................................................................................
.....................................................................................
.....................................................................................
....................................................................................
....................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================

./ati-installer.sh: 156: Syntax error: Bad substitution

Removing temporary directory: fglrx-install

user@user-laptop:~$

```

Ubuntu 7.10 on Toshiba Satellite A105S2001 Radeon Xpress 200

---

### Post by erfahren on 2008-02-07
**cdcweb** - that guide is a little dated - try this guide, it's better maintained - you may get better results (its for Dapper)
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by cdcweb on 2008-02-07
Thanks for the link, however I still get a stall at **Method 1** in the instructions at;
```

user@user-laptop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@user-laptop:~$ sudo depmod -a
user@user-laptop:~$ sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
user@user-laptop:~$ 

```
I have no unix programming experience, so I have no idea where I'd have to copy from or even how to do it.

**Method 2** fails on that page as well, as the module cannot be compiled. Instructions are unclear. I'm guessing I'm supposed to enter my Kernel version in a *(version)* statment in the code, but I'm unsure if I'm supposed to enter that (if I even knew) or *(version)* literally.

Caveats to errors are further down the page, when they should be near the error that may come up.

I consider myself a power user on computers, but even all these hoops are a lot for even me to jump through. I want to use Linux badly, but the non-standards so far, including differing tutorials, is making my head spin.

---

### Post by erfahren on 2008-02-07
oh - I apologize! -- actually the original post on this thread is for Dapper (Ubuntu 6.06) -
I just saw the line: "./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper" and assumed that you were using Dapperl (and was using that HowTo because of that).

I just now noticed that you said "Ubuntu 7.10 on Toshiba Satellite A105S2001 Radeon Xpress 200" at the bottom of your post. -- I'm sorry!!!

try this guide (same one, but for Gutsy) - "Method 2": [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

note: from your output from the Method 1 install that you posted, you already have the version of the ATI driver ("fglrx") that comes with Gutsy. 
you should see the version (and if it's working) by entering into the terminal:
```

fglrxinfo

```
anyway, if you want the newer version of the driver go with the guide I just posted. It's for Gutsy (and it should be easier).

again - I apologize!

---

