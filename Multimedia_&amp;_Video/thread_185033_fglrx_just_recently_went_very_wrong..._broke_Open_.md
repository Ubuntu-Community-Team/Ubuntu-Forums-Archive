---
title: "fglrx just recently went very wrong... broke Open Office?!"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by mattisking on 2006-05-31
I'm rather recently having some very strange ATI problems. I'm not certain if this came with the last fglrx driver update or some time afterwards but now I can't run any of the OpenOffice applications, nor can I run the command fglrxinfo. Doing either gives me this:

```
:~$ ooffice -writer %U [fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS [fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
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

** (process:8384): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

I've rebuilt my xorg.conf starting over with it and then using aticonfig --initial to get it going again. X is working fine in general... I don't have a clue here.

---

### Post by nodgesoft on 2006-05-31
Same problem here - was working a few days ago and I havent changed anything - must have been the update.

Anyone know how to fix it?

-Matt

---

### Post by Kindred on 2006-05-31
The latest ATI drivers are broken with r200 cards it seems. 

[http://ati.cchtml.com/show_bug.cgi?id=373](http://ati.cchtml.com/show_bug.cgi?id=373) 
[http://rage3d.com/board/showthread.php?t=33856854](http://rage3d.com/board/showthread.php?t=33856854)

i'm just using the older drivers for now... hopefully they'll fix it in the next release or something.

---

### Post by joshrobinson on 2006-05-31
you can copy the old libGl.so.1.2 over your current one.. that fixes the problem

i can upload the file if you need it.. its for the version before this one.. that should fix you up

---

### Post by z3snap on 2006-05-31
^^ that would be very helpful, thank you

---

### Post by joshrobinson on 2006-05-31
[QUOTE=z3snap]^^ that would be very helpful, thank you[/QUOTE]

[http://www.ground-impact.com/libGL.so.1.2]("http://www.ground-impact.com/libGL.so.1.2")

probibly going to have to right click it and save target as.. it might open up thinking its text in firefox

edit: im pretty sure you replace this with the one in /usr/lib/libGL.so.1.2.. then run fglrxinfo again.. if that doesnt work replace the file i hosted with any other libGL.so.1.2 you find

---

### Post by marksnelling on 2006-05-31
I was also having this problem. It did indeed seem to break with the last fglrx update.
Replacing libGL.so.1.2 with the one you posted did the trick thanks :D

---

### Post by joshrobinson on 2006-05-31
your welcome.. glad you got it working 8)

---

### Post by caldevil on 2006-05-31
Thaks joshrobinson. You solved the problem for lot of us. There was a bug filed on launchpad about this:
[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/47371/+index](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/47371/+index)

---

### Post by joshrobinson on 2006-05-31
glad to help :-D..the link to the file should stay for a good while.. so whoever needs to download please do

---

### Post by Ivhassel on 2006-05-31
[QUOTE=joshrobinson][http://www.ground-impact.com/libGL.so.1.2]("http://www.ground-impact.com/libGL.so.1.2")

probibly going to have to right click it and save target as.. it might open up thinking its text in firefox

edit: im pretty sure you replace this with the one in /usr/lib/libGL.so.1.2.. then run fglrxinfo again.. if that doesnt work replace the file i hosted with any other libGL.so.1.2 you find[/QUOTE]

Thank you very much for this :)

---

### Post by Kindred on 2006-05-31
Would anyone know if using that older file negates any/all of the benefits of the newer drivers?  Just a thought because I have no idea..

---

### Post by phorque on 2006-05-31
At last! I couldn't find any previous versions on my harddrive so thanks for saving the day for me!

---

### Post by Ivhassel on 2006-05-31
[QUOTE=Kindred]Would anyone know if using that older file negates any/all of the benefits of the newer drivers?  Just a thought because I have no idea..[/QUOTE]

If it's not broke, don't fix it. 
If it's broke, then what benefits are we talking about ? :D

---

### Post by Amt0571 on 2006-05-31
I've solved it replacing the libGL, Thanks!!!

Now, I think I'm going to buy an nVidia card... I'm tired of ATi's crap...

---

### Post by dudus on 2006-05-31
I'd rather wait for the fix. Even if it is backported.
That's sad that my graphic adapter have been working since flight 1 and now I get this, 2 days from final release. 
Maybe it's time to spend some bucks on an nvidia card. It's sad it's because of configuration instead of lack of drivers.
Bad Mantainer

---

### Post by joshrobinson on 2006-05-31
your welcome everyone... lets just hope they put out an official fix soon:confused:

---

### Post by seth0x2b on 2006-05-31
It works!
Thank you! Thank you! Thank you!
Replaced /usr/lib/libGL.so.1.2 with this one and fglrx is back to normal!
I have a question for you guys.
On Hoary I used this [http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+issue](http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+issue) to get my 9200SE up and running, and fgl_glxgears was doing about 700-800 FPS.
On Breezy, and now on Dapper, I only get about 130 FPS.
Has anyone had this issue before, and if so, how did they fix it?!

Thanks alot!
Cheers

---

### Post by tukuyomi on 2006-05-31
[QUOTE=joshrobinson][http://www.ground-impact.com/libGL.so.1.2]("http://www.ground-impact.com/libGL.so.1.2")

probibly going to have to right click it and save target as.. it might open up thinking its text in firefox

edit: im pretty sure you replace this with the one in /usr/lib/libGL.so.1.2.. then run fglrxinfo again.. if that doesnt work replace the file i hosted with any other libGL.so.1.2 you find[/QUOTE]
Thanks joshrobinson, the old libGL fixed my problem too =)

---

### Post by joshrobinson on 2006-05-31
[QUOTE=tukuyomi]Thanks joshrobinson, the old libGL fixed my problem too =)[/QUOTE]

:D :D

---

### Post by jstritar on 2006-05-31
Thanks that fixed my problem too-- hopefully they fix fglrx before releasing Dapper!

---

### Post by Nicksha on 2006-06-02
It works for me too. Thank you! I pointed to this on the couple of other threads.

---

### Post by toran on 2006-06-02
YOU FIXED MY PROBLEM.

Score. Major score.

---

### Post by sumadartson on 2006-06-03
[hyperbole] Words cannot express my gratitude [/hyperbole]

---

### Post by toran on 2006-06-03
The problem started up again, and this time the libGL.so.1.2 isn't fixing it, even after I re-downloaded and re-copied it. What should I do?

---

### Post by sumadartson on 2006-06-03
Same here. This is weird.

---

### Post by jonboy99 on 2006-06-03
Me too!  copied it to the /usr/lib folder, but there wasn't any file of the same name to overwrite.  It didn't make any difference.

[Edit] I think i copied it to the /usr/bin library by mistake.  copied it to the /usr/lib and /usr/lib/fglrx too for good measure and is working.

---

### Post by jmercer on 2006-06-03
Just wanted to say thanks. I've been fighting with this one for days now.

---

### Post by sumadartson on 2006-06-03
Managed to fix it on my own pc. 

I Installed the drivers from [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") and not only copied the libGL.so.1.2 from this thread, but also updated the libGL.so.1 link. 

Oddly enough, the link was pointing to a backup version of the old libGL.so.1.2.

](*,)

---

### Post by cjtenny on 2006-06-03
woohoo thanks!
now i can play unreal.

unfortunately i reinstalled ubuntu before finding this thread.  still, i got to try the new release + xubuntu.  so it's all good.

---

### Post by Stinko on 2006-06-04
Finalmente funzionano! :mrgreen: 

Ecco come ho fatto:

1) Installare Dapper, abilitare tutti i repo standard e aggiornare il sistema

2) Scaricare questi driver nel Desktop:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run)

3) Installare il necessario per la compilazione:
```
sudo apt-get update
sudo apt-get install module-assistant build-essential debhelper gcc-3.4
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```

4) Generare i pacchetti:
```
cd ~/Desktop
chmod +x ati-driver-installer-8.24.8-x86.run
LANG=C LC_ALL=C ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper
```

5) Editare questo file:
```
sudo nano /etc/default/linux-restricted-modules-common

Modificare questa riga:
DISABLED_MODULES=""
in
DISABLED_MODULES="fglrx"
```

6) Installare i pacchetti che abbiamo generato al §4:
```
sudo dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb
sudo dpkg -i fglrx-control_8.24.8-1_i386.deb
```

7) Rimuovere fglrx-kernel*.deb (non ci dovrebbe essere niente)
```
sudo rm /usr/src/fglrx-kernel*.deb
```

8 ) Compilare:
```
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx
sudo depmod
```

9) Correggere  /etc/X11/xorg.conf
```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

10) Riavviare il sistema:
```
sudo reboot
```

11) Primo test:
```
fglrxinfo
```

12) Secondo test:
```
fgl_glxgears
```

13) Fare un bel sorriso! ;D

Ecco i risultati dei miei test:
```
stinko@stinko-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1060 (X4.3.0-8.24.8)

stinko@stinko-desktop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
641 frames in 5.0 seconds = 128.200 FPS
798 frames in 5.0 seconds = 159.600 FPS
818 frames in 5.0 seconds = 163.600 FPS
791 frames in 5.0 seconds = 158.200 FPS
823 frames in 5.0 seconds = 164.600 FPS
790 frames in 5.0 seconds = 158.000 FPS
807 frames in 5.0 seconds = 161.400 FPS
787 frames in 5.0 seconds = 157.400 FPS
823 frames in 5.0 seconds = 164.600 FPS
795 frames in 5.0 seconds = 159.000 FPS
797 frames in 5.0 seconds = 159.400 FPS
817 frames in 5.0 seconds = 163.400 FPS
790 frames in 5.0 seconds = 158.000 FPS
stinko@stinko-desktop:~$

```

Questo è il mio attuale * /etc/X11/xorg.conf* (vedi *Section "Device"*)
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
	Option	    "XkbLayout" "it"
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
	Identifier   "L1950S"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor    "L1950S"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
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

Vedi:
[http://forum.ubuntu-it.org/index.php?topic=25266.0](http://forum.ubuntu-it.org/index.php?topic=25266.0)

---

### Post by gumbald on 2006-06-04
I've replaced the file... now I when I run fglrxinfo or glxgears I simply get:

```
Bus error
```

Any thoughts?

---

### Post by iheartmuseums on 2006-06-05
[QUOTE=joshrobinson][http://www.ground-impact.com/libGL.so.1.2]("http://www.ground-impact.com/libGL.so.1.2")

probibly going to have to right click it and save target as.. it might open up thinking its text in firefox

edit: im pretty sure you replace this with the one in /usr/lib/libGL.so.1.2.. then run fglrxinfo again.. if that doesnt work replace the file i hosted with any other libGL.so.1.2 you find[/QUOTE]


Thanks so much - fixed mine with no problems! :)

---

### Post by kyke on 2006-06-05
Thanks joshrobinson, worked fine for me too ;)

---

### Post by joshrobinson on 2006-06-05
[QUOTE=kyke]Thanks joshrobinson, worked fine for me too ;)[/QUOTE]

:-D

---

### Post by kokas on 2006-06-05
I don't seem to be able to download the file....can anyone please send it to me ?? [email]neldiogo@gmail.com[/email]

---

### Post by m1d_kn1ght on 2006-06-06
Hi all.

I too had this problem.  This seems to have fixed it nicely :D 

To help try and keep this alive, Ive also hosted a copy of the file.

This is a great fix.  Kudos to those who came up with it.

Here is is : [http://nicksplace.mine.nu/downloads/libGL.so.1.2]("http://nicksplace.mine.nu/downloads/libGL.so.1.2")

Again, you may have to right click "Save link as"

Cheers for all your help guys!

MK

---

### Post by kokas on 2006-06-06
[QUOTE=kokas]I don't seem to be able to download the file....can anyone please send it to me ?? [email]neldiogo@gmail.com[/email][/QUOTE]


I have the file already and it worked...thanks :D

---

### Post by gorgor_bay on 2006-06-06
I still have issues despite all the advices in this thread :

```
$ fglrxinfo
Error: couldn't find RGB GLX visual!
```

Whereas 3D acceleration was properly working before the last drivers update.
So I copy the old **libGL.so.1.2** linked here :

```
$ sudo cp ~/libGL.so.1.2 /usr/bin/libGL.so.1.2
```

But then I get :

```
$ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

So I check the symbolic link :

```
$ ls -la libGL.so.1
lrwxrwxrwx 1 root root 12 2006-05-30 08:28 libGL.so.1 -> libGL.so.1.2
```

that is present and has proper permissions...
now I don't know what to do, if any of you guys has an idea, it will be welcome !

---

### Post by sbaush on 2006-06-06
Reassuming...
To have FGLRX working in dapper:
```

sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo nano /etc/X11/xorg.conf
```
Now replace this line
```
Driver "ati"
```
with:
```
Driver "fglrx"
```
save and exit.
Then
```
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```

This should be OK, so try reboot and run fglrxinfo.
If you have the FGLRX problem of this post you can do this: (Thanks to *joshrobinson*)
```
cd ~
wget http://www.ground-impact.com/libGL.so.1.2
cd /usr/lib/
sudo mv libGL.so.1.2 libGL.so.1.2-BAK
cd ~
sudo mv libGL.so.1.2 /usr/lib/
```
Now reboot and enjoy with GL!!

---

### Post by gorgor_bay on 2006-06-07
Well I allready have the flgrx driver in xorg.conf instead of the ati driver, so your proposal for a solution is not working unfortunately...

---

### Post by highslime on 2006-06-07
Heh, I just tried to update the drivers and had the exact same thing happen to me.  Seeing API errors freaked me out :(  luckily i got it fixed, now time to go break something else on accident :D

---

### Post by Matze on 2006-06-07
Thank you, joshrobinson!
You solved my probem!!! :-D
Forever yours ;-)

---

### Post by highslime on 2006-06-08
Heh, it didn't take me long.  I got the video stuff working, so then I thought I'd give compiz a whirl.  Well either I did something wrong, or compiz doesn't run on a Radeon 9250.  Oh well, 3D accel is enough for me, I don't need spinning cubes and bent movies. :D

---

### Post by atha on 2006-06-09
> 
```
$ sudo cp ~/libGL.so.1.2 /usr/**bin**/libGL.so.1.2
```

[QUOTE=gorgor_bay]Well I allready have the flgrx driver in xorg.conf instead of the ati driver, so your proposal for a solution is not working unfortunately...[/QUOTE]

You seem to have copied it to wrong directory, copy (or move) into /usr/lib.

---

### Post by gorgor_bay on 2006-06-09
Yes this is right, but still :

```
$ ls -la /usr/lib/libGL.so.1*
lrwxrwxrwx 1 root root     12 2006-06-07 14:00 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rwxrwxrwx 1 leo  leo  635084 2006-06-09 14:17 /usr/lib/libGL.so.1.2
-rw-r--r-- 1 root root 771088 2006-05-29 14:54 /usr/lib/libGL.so.1.2-BAK

```

```
$ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

This is really strange ](*,)

---

### Post by kochab on 2006-06-10
Thanks,
worked great also on my dapper with ati radeon 9100 R200 QM! :p

---

### Post by damko on 2006-06-10
it works for me in this way

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/47371/+index](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/47371/+index)

bye!

---

### Post by akniss on 2006-06-13
Thanks to the OP!!!  This fixed my problem as well...  However, it only works until i restart X with ctrl+alt+backspace.  then I get mesa again and I've lost 3d.  Any idea how I get the fix to follow me through an X restart?

---

### Post by danoyoto on 2006-06-14
OK, I am at a loss!  I followed the instructions and installed the 8.25 drivers, then replaced my libGL and it worked!  Everything was running great!  Then I plugged in the VGA cord to my TV-OUT to see if it was working, rebooted and my monitor came up with whacked out colours!  The gamma seems way bright.  So I unplugged the TV, rebooted and the colour was good!  Cool, back to normal.......NOT.  FGLRX is broke again!  I don't know what happened or why!  Please, any help?

---

### Post by Turin Turambar on 2006-06-14
I just replaced the libGL and now everything is working fine!!
I just couldn't get fglrx to load/work!! Now I have a 3D support. I guess, the fglrx drivers are buggy.

---

### Post by joshrobinson on 2006-06-14
woah, just checked back on this thread after awhile.. man i feel all special and popular for fixing all these peoples problems :D makes me feel all warm and gooey inside

---

### Post by joshrobinson on 2006-06-14
/ground-impact/libGL.so.1.2	4,216	Requests


woah.. thats alot of downloads of that file :D

---

### Post by SteinbergerNate on 2006-06-15
I got it working yesterday with this download and then there was an update ready this morning. I thought "Oh, maybe this is the official fix for the problem." Nope. It's broke again and the old file doesn't fix the problem :sad:

---

### Post by danoyoto on 2006-06-15
did you get it fixed?  I reinstalled my system this morning and tonight I will be redoing all the steps here to get things working again, althoug I may just leave everything as default for awhile and see what else comes up on the post....

---

### Post by Turin Turambar on 2006-06-15
[QUOTE=SteinbergerNate]I got it working yesterday with this download and then there was an update ready this morning. I thought "Oh, maybe this is the official fix for the problem." Nope. It's broke again and the old file doesn't fix the problem :sad:[/QUOTE]

Sorry to hear that. So it's not possible to fix "new" xorg-fglrx with the old file? :(
This just gets worse and worse.
I just wanted to perform the updates - kernel and stuff, but wait - no way I'll do that now. Not until ATI cleans the mess!!

---

### Post by joshrobinson on 2006-06-15
[QUOTE=Turin Turambar]Sorry to hear that. So it's not possible to fix "new" xorg-fglrx with the old file? :(
This just gets worse and worse.
I just wanted to perform the updates - kernel and stuff, but wait - no way I'll do that now. Not until ATI cleans the mess!![/QUOTE]

i havent gotten a new xorg-fglrx update.. weird.. my laptop and my desktop i fixed the way i posted, and are still running normal

---

### Post by daahli on 2006-06-16
Same problem here. I had fixed it by using the old file, but today's update broke it again, and now the old file trick no longer works :(

---

### Post by sumadartson on 2006-06-16
Hmmm... radeon 9200se here, but everything still works fine. No clue why.

It just seems to me that ATI really isn't putting any effort into these drivers. It's so bad that I'm going to buy a nvidia card just out of spite. And the ability to run xgl+compiz on two monitors.

---

### Post by 5hundy on 2006-06-16
This situation is unfortunate. As a temporary fix I downgraded the xorg-driver-fglrx package in synaptec (Package -> force version) to version ...2.6.15.11-1. Then as root I went to the /usr/lib dir and removed the libGL.so.1.2 file. Finally I did a wget [http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2)

For now I think I'll lock the version in synaptic until I hear this is fixed.

---

### Post by joshrobinson on 2006-06-16
[QUOTE=5hundy]This situation is unfortunate. As a temporary fix I downgraded the xorg-driver-fglrx package in synaptec (Package -> force version) to version ...2.6.15.11-1. Then as root I went to the /usr/lib dir and removed the libGL.so.1.2 file. Finally I did a wget [http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2)

For now I think I'll lock the version in synaptic until I hear this is fixed.[/QUOTE]

yeah i would do what 5hundry here did.. sounds like the new driver has a new set of problems

---

### Post by haxor999 on 2006-06-17
hi, i had applied the fix (download libGL.so.1.2, move old libGL.so.1.2 to libGL.so.1.2.old, and put the new one in it's place), and all was well.

today i upgraded my system, and as with other people, 3d was broken again. guess what happens? as one poster mentions above, I found that the libGL.so.1 symbolic link in /usr/lib/ was pointing to the _old_ copy of libGL: it was actually pointing now to libGL.so.1.2.old!! strange behavior... i guess the installer verifies which file it's making the symbolic link point to?

solution: check all your libGL-related symlinks (cd /usr/lib; ls -l libGL*) and make sure they are pointing to the right libGL.

3d's now working again here.

---

### Post by Turin Turambar on 2006-06-17
.............. I installed the newest xorg-fglrx and, of course, didn't work. I just copied the old libGL and now works again without any problems. :)

My ATI is Radeon 9000PRO.

---

### Post by will_Power on 2006-06-17
The problem with the old file not working after rebooting is because Linux resets the symbolic links (ldconfig) during every boot. ldconfig checks library versions and sets links to the correct ones, hence causing the libGL.so.1.2.old (which is the new libGL that doesn't work) file to be linked to libGL.so.1. Note that this is normal and desireable behavior in most (read: all) cases, with the exception of this one, due to ATI's lack of testing of their product.

I added a couple of lines to rc.local to fix this:

rm /usr/X11R6/lib/libGL.so.1
ln -s /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so.1

Depending on your distro, you may have to use a different path to libGL:

rm /usr/lib/libGL.so.1
ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

Hope this helps!

---

### Post by d3xter on 2006-06-17
Hi. I repackaged original binary package with this old libGL.so. You can download with following APT source:

## Fixed ATI driver
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) xorg-driver-fglrx dapper

---

### Post by Dubbayoo on 2006-06-17
This fix also worked for me although 3D perf still seems fairly poor. I have a Radeon 8500 128MB.

steve@ubu-6:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1738 frames in 5.0 seconds = 347.600 FPS
2132 frames in 5.0 seconds = 426.400 FPS
2109 frames in 5.0 seconds = 421.800 FPS
2125 frames in 5.0 seconds = 425.000 FPS
2114 frames in 5.0 seconds = 422.800 FPS

---

### Post by brickhead20 on 2006-06-18
This is very gay. I was also hoping for the new driver on the update to fix the rebooting freeze problem that everyone seems to get, where it freezes on shutdown. Its a pain that it jams up OpenOffice, because apart from the somewhat oddball unreliable double-sided printing support, its these irritating bugs which keeps my windows partition in existance.

Damn you ATI. How hard can it be to get it working and actually test it? Surely they know their own hardware by now.

---

### Post by sumadartson on 2006-06-18
This is embarassing... I got so fed up with nothing working properly on ati I actually bought an nvidia card. :( 

Now... To let both ati and nvidia know this... Does anyone know the "customer feedback" adres of both chip manufacturers? We can at least let them know they have a linux userbase, right?

---

### Post by sumadartson on 2006-06-18
[https://support.ati.com/ics/support/default.asp?deptID=894](https://support.ati.com/ics/support/default.asp?deptID=894)

Seems to provide some information for ati.

Just search for feedback and you can quickly find an entry for "linux driver feedback"

---

### Post by Cerealz on 2006-06-19
> **joshrobinson]
[http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2)

probibly going to have to right click it and save target as.. it might open up thinking its text in firefox

edit: im pretty sure you replace this with the one in /usr/lib/libGL.so.1.2.. then run fglrxinfo again.. if that doesnt work replace the file i hosted with any other libGL.so.1.2 you find [/QUOTE]

Thanks  josh !! it worked for me too  said:**
> I've replaced the file... now I when I run fglrxinfo or glxgears I simply get:

```
Bus error
```

Any thoughts?

gumbald..try to download the file again..and check if its 620.2 KB ... because i had the same problem.. and it was from my laggy connection...that was completing the transfer before its end.

---

### Post by mszkutnik on 2006-06-21
Well, I downloaded the recommended version of libGl shared library, and here is what I get when running fglrxinfo:
ERROR: DDX driver fingerprint mismatch: got 0xC20D27F9, but expected 0x32C4A39B
libGL error: InitDriver failed

:/ Any ideas?

---

### Post by mustang on 2006-06-24
Thank you joshrobinson. Fixed the problem!

---

### Post by joshrobinson on 2006-06-24
[QUOTE=mustang]Thank you joshrobinson. Fixed the problem![/QUOTE]

:-D 

up to 7,612 requests on that file now.. i hope i at least helped 75% of that

---

### Post by BeatBoxRocker on 2006-06-26
Please, Could someone post another mirror for the file libGL?? I have tried more than ten times to download it but I cant download more than 500kb of the file (maybe my 56kb connection).

Thanks in advance! Saludos!

Edit: I have just downloaded the Deb package and extracted the file.  It works perfectly!!! :)

---

### Post by kthakore on 2006-06-27
with the recent upgrade of the fglrx module I put the libgl file but I get this error

```
fglrxinfo
ERROR: DDX driver fingerprint mismatch: got 0xC20D27F9, but expected 0x84220BA7
libGL error: InitDriver failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

---

### Post by Cavalera on 2006-06-27
I get a simular error message, although it is slightly different. Any ideas?

ERROR: DDX driver parameter mismatch: got 800 bytes, but expected 832 bytes.
libGL error: InitDriver failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

### Post by joshrobinson on 2006-06-27
[QUOTE=BeatBoxRocker]Please, Could someone post another mirror for the file libGL?? I have tried more than ten times to download it but I cant download more than 500kb of the file (maybe my 56kb connection).

Thanks in advance! Saludos!

Edit: I have just downloaded the Deb package and extracted the file.  It works perfectly!!! :)[/QUOTE]

yeah it must be your connection or something.. at least you got the file tho.. its had about 8,500 requests for it so far now.. so i can tell it has been working for alot of people

---

### Post by campa on 2006-07-04
Work also for me, thank you very much !!

---

### Post by Cheule on 2006-07-05
Sadly it didn't work for me, I replaced the libgl file with the one available for download, and after rebooting, I get a black screen with a grey dialox box which has gibberish printed on it, mostly control characters. Pressing what I presume to be the "OK" button, I'm dumped at the command-line login.


Is there a way for me to get the old file back from the install disc?

---

### Post by mwells on 2006-07-08
Yup, just to say this solved my problem as well . . 

I would also agree with others that i shall be sticking firmly to nvidia from now on. . ATI seems to be issue after issue . . .

Also is there any ideas as to when this will be 'officially' sorted? . .i.e. new (actually working) driver releases?

many thanks joshrobinson for solving this for me!

/Matt

---

### Post by Cheule on 2006-07-11
> **Cheule said:**
> Sadly it didn't work for me, I replaced the libgl file with the one available for download, and after rebooting, I get a black screen with a grey dialox box which has gibberish printed on it, mostly control characters. Pressing what I presume to be the "OK" button, I'm dumped at the command-line login.


Is there a way for me to get the old file back from the install disc?

Never mind, I figured what I did wrong, I'd forgotten to symlink to the new libGL file. Doh.:mrgreen:

---

### Post by MartynM on 2006-07-12
My flglrx just auto updated along with the open office suite, now open office no longer works, and neither does Blender. I'd been holding off from installing fglrx but couldn't get any video to work without it, I installed it last night and immediately got the auto update message. Is this still the same update that is the subject of this thread? If so, why is it still active!

I must adnit, I'm still really green when it comes to Linux, only been running this install for a couple of weeks. Most of the fixes in this thread are a little beyond my current knowlege, does anyone know when this is likely to be fixed? The easiest solution that I can think of is to go and buy an Nvidea card.

Are the fixes in this tread still valid? If so, would somebody be so kind as to dumb them down into newbie terms for me.

Cheers

M

---

### Post by didu on 2006-07-12
Hi guys,

I found something rather strange here. I just followed the wiki page to install the the ati 8.26 driver for my mobility radeon 9000, everything worked except for the "annoying [fglrx] API ERROR: could not register entrypoint for XXX" errors, I then followed the direction posted in the first page of this thread to replace the libGL.so.1.2 library and that fixed the "could not register entrypoint for XXX" errors, however, when I ran fgl_glxgears, I only saw a grey rotating cube, instead of the cube with lots of spinning gears on each face. Is this normal?

Thanks a lot.

-D

---

### Post by hamid.nyc on 2006-07-13
[FONT="Arial"]After this morning's update, open office died on me again. I copied the libGL.so.1.2 from this thread and put it in the /usr/lib and /usr/lib/fglrx folders but that didn't work either. I noticed earlier in sumadartson's reply that the libGL.so.1 link was pointing to the libGL.so.1.2.bak file, strange as that seems. So, I took the libGL.so.1.2 link from this thread, put it into both the above folders and renamed it with .bak, I also put the libGL.so.1 from /usr/lib into /usr/lib/fglrx also. That worked finally, try it and let me know...[/FONT]

---

### Post by dagopher on 2006-07-16
Ok - I finally got my 9600 Pro (256Mb) working with Kubuntu 6.06 LTS. (While I did this with Kubuntu, I'm sure it probably works with the other releases as well, none of this stuff to my knowledge is KDE specific.)

The short version was to add this line to my 'Device' section in xorg.conf:
        [INDENT]Option          "BusType" "PCI"[/INDENT]

I'm not sure, but I'm really starting to wonder if this wasn't just a goof up with the AGP handling in the driver.  Who knows.

Here's my step-by-step to fix my system: 

- Install stock Kubuntu 6.06 off Live CD
- Reboot system
- Install FireGL drivers. Follow 'Method 1' from [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide:](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide:)
[INDENT]   sudo apt-get update
  sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it   is already installed
   sudo apt-get install xorg-driver-fglrx
   sudo depmod -a
   sudo aticonfig --initial
   sudo aticonfig --overlay-type=Xv[/INDENT]

- Reboot ### MAKE SURE YOU DO THIS - IT AVOIDS LOTS OF HEADACHES LATER
- After system boots, check /var/log/Xorg.0.log.  You may have AGP related issues. I did. I found the following errors, and needless to say performance on my system sucks big rocks.

[INDENT](WW) RADEON(0): [agp] AGP not available[/INDENT]
[INDENT](EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
[/INDENT]
- If you do NOT see these errors, you may be done.  Check with 'fglrxinfo' and 'fgl_glxgears'.  

- Edit /etc/X11/xorg.conf, add BusType option.  Make your 'Device' section like this:

[INDENT]   Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "BusType" "PCI"
   EndSection[/INDENT]

- Reboot (or just re-start X)
- Check /var/log/Xorg.0.log for AGP errors.  I Found none at this point:

[INDENT](II) fglrx(0): AGP card detected
(**) fglrx(0): Forced into PCI mode[/INDENT]

- Ran 'fglrxinfo', got the following:

[INDENT]   $ fglrxinfo
   display: :0.0  screen: 0
   OpenGL vendor string: ATI Technologies Inc.
   OpenGL renderer string: RADEON 9600 XT Generic
   OpenGL version string: 2.0.5814 (8.25.18)
[/INDENT]
- Ran 'fgl_glxgears' with the following results:
[INDENT]   1) It ran (this was a first on my system)
   2) Was seeing between 350-600 FPS - WOO![/INDENT]

Once I got fgl_glxgears running, I was happy.  Up until now, I couldn't even get it to start without dying immediately.  Now it seems to be just fine.

I never once used any copies of previous drivers - so unless somebody updated the fglrx packages in the repository the forcing of the BusType fixed everything for me.

I found this by digging through other forums related to the same basic problem.

Hope this helps somebody.

thx
Gopher.

---

### Post by skyshock21 on 2006-07-17
HEY, whoever's maintaining the fglrx package?  QUIT BREAKING MY DIRECT RENDERING!  Is it really that hard to to include the proper libGL.so.1.2 file along w/ the driver?  Or at least keep from overwriting it each time?  Every update keeps borking my screen... 

Sorry for the rant, but really, it's getting OLD.  

](*,) ](*,) ](*,)

---

### Post by gumbald on 2006-07-18
I agree, surely there's enough people have come across this problem for somebody to take note and sort it...?

---

### Post by JedTheHead on 2006-07-18
My OO seems to be OK, but I still cannot get direct rendering working again after last weeks fglrx driver update.  I have tried many things, including (and starting with) re-replacing libGL.so.1.2.  (This is what made things woork before the last update).  I would rip this ATI POS out of this machine in a heartbeat if I could, but alas, its a laptop.  

I'm stuck with Mesa rendering at the moment.  Any ideas?!?!?

```

xxxxx@xxxxx:~$ ls -al /usr/lib/libGL*

lrwxrwxrwx 1 root root     16 2006-03-27 11:53 /usr/lib/libGLEW.so.1.3 -> libGLEW.so.1.3.1
-rw-r--r-- 1 root root 205204 2005-11-30 15:47 /usr/lib/libGLEW.so.1.3.1
lrwxrwxrwx 1 root root     10 2006-07-03 23:16 /usr/lib/libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root     12 2006-07-12 09:12 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 635084 2006-07-18 09:18 /usr/lib/libGL.so.1.2
-rw-r--r-- 1 root root 635084 2006-07-12 15:01 /usr/lib/libGL.so.1.2.bak
lrwxrwxrwx 1 root root     20 2006-07-03 23:16 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.060500
-rw-r--r-- 1 root root 483308 2006-06-28 15:21 /usr/lib/libGLU.so.1.3.060500

```

```

xxxxx@xxxxx:~$ ls -al /usr/lib/fglrx/*

-rw-r--r-- 1 root root 635084 2006-07-18 09:19 /usr/lib/fglrx/libGL.so.1
-rw-r--r-- 1 root root 635084 2006-07-18 09:18 /usr/lib/fglrx/libGL.so.1.2
lrwxrwxrwx 1 root root     15 2006-07-18 09:27 /usr/lib/fglrx/libGL.so.1.2.xlibmesa -> ../libGL.so.1.2
-rw-r--r-- 1 root root 410880 2006-06-28 15:21 /usr/lib/fglrx/libGL.so.1.2.xlibmesa.bak
lrwxrwxrwx 1 root root     15 2006-07-05 13:05 /usr/lib/fglrx/libGL.so.1.xlibmesa -> ../libGL.so.1.2

```

As seen in the last one, I also tried linking /usr/lib/fglrx/libGL.so.1.xlibmesa -> ../libGL.so.1.2, but that hasn't changed anything either.

Thanks!

---

### Post by taladon on 2006-07-23
Thanks, that fixed the problem for me also.
This has been my first serious foray into Linux, and it's really been fun.

---

### Post by tuxlookalike on 2006-07-26
Googled. Found your thread. Now I´m happy again! Thank you!

---

### Post by Dubbayoo on 2006-07-26
I just added the following to the end of /etc/rc.local. I believe I found the good copy of libGL.so.1.2 on one of these threads. 

> 
# for ATI driver
cp /data/backup/steve/libGL.so.1.2 /usr/lib/
exit 0


---

### Post by iheartmuseums on 2006-08-02
Thanks for the fix, Josh! Openoffice is back up and working again. Cheers :)

---

### Post by cazub on 2006-08-03
[I"]Managed to fix it on my own pc. 
 
 I Installed the drivers from [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide) and not only copied the libGL.so.1.2 from this thread, but also updated the libGL.so.1 link. 
 
 Oddly enough, the link was pointing to a backup version of the old libGL.so.1.2.[/I]"



The original idea to replace libGL.so.1.2 worked .......for about a day and a half and then i got the API errors again.

thanks to sunderstrom , fixing  libGL.so.1 link so that it points to the new libGL.so.1.2 did the trick, woot woot woooooooot

---

### Post by pau on 2006-08-08
Hi,

I am having some touble with this issue... I just posted it to another thread:

[http://ubuntuforums.org/showthread.php?p=1354158#post1354158]("http://ubuntuforums.org/showthread.php?p=1354158#post1354158")

Can you please have a look?

This ati thing is driving me crazy...

---

### Post by pau on 2006-08-09
HELP! I don't understand anything! I followed the installation guide step by step and fixed the links and I am still stuck to mesa3d! 

```
andromina| ls -lart /usr/lib/libGL.so.1                                                                                                                    
lrwxrwxrwx 1 root root 12 2006-08-08 11:26 /usr/lib/libGL.so.1 ->libGL.so.1.2

andromina| fglrxinfo                                                                                                                                       
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

Any hint??

---

### Post by pau on 2006-08-09
Well, that makes it

Go to hell, ATI

If it's not open, it's not good for you

The answer: Never buy again anything from ATI

I feel like begging ATI to give me what I paid for. If they're on the side of windows and propietary software, they can just FO

---

### Post by parsons151185 on 2006-08-15
I asuming most people are complain about ATi's older cards. Graphics Cards move so quickly they they cant support them for ever,even for windows the 8x00-9200 arn't officaly supported 9500 and above are.

ATI have improved their linux drives quite alot, just a shame they screwed up the drivers for some of the cards. its not that difficult to lock the version of the drivers in SMP, I have only been using Ubuntu for a month now and it just on my laptop what hardly gets used and had a Radeon 9000 in it. I would imaging we won't see that much action on the driver front until everything is sorted with AMD, then we could see some big changes, least thats my opinion.

Oh I nearly forgot. I have been playing games on Ubuntu using Wine, the ammount of comments on [www.winehq.com](www.winehq.com) were users have come across issues with NVidia cards having problems, its not just ATI.

there is also an [offical fix](https://support.ati.com/ics/support/KBAnswer.asp?questionID=22637) on ATIs site which is the same as what is on the forum

---

### Post by SniperSlap on 2006-08-17
This is BS.
I'm using an ATI 8500LE while the replacement for my 6600GT is on it's way back from BFG.
(All you ATI fanboys, rest assured, this 8500LE's fan started to die shortly after I bought it and is now fanless.)

I figured now would be a good time to scope out the driver scene for this little card....So basically we're reverting back to software rendering for this card?  Yet NVidia can still support a TNT2?!  Or even a RIVA?!?

ATI drops the ball again because...?  Business administration demands reduction in quality to score investor interest?  I betcha ATI ships with UPS too...

I have never liked ATI's cards after my VGA Wonder.  They're just too confusing and poorly architected.  When I was younger, my family got me a Rage PRO as opposed to a decent 3DFX addon card for a gift.  Boy was that a lousy year of paltry performance and lack of support.  As soon as I rustled up the cash I got a Banshee.  It was cheap, fast and hey - at least it was supported!!

Many years later...I have worked at wholesale computer stores and I can now attest to ATI's sh!ttyness.  Fanboys buy these cheap video cards because some review site sat there praising them for clock speeds and "oh boy, buy a few models down for half the price and overclock it!".  The hallmark of ATI.  Glitchy fanboy video cards with no real merit over the features NVidia tries to pack into their cards.  Hell, they even upped the ante on 2D with PureVideo.

There is no reason why ATI should use Linux driver support as an arm of marketing to push newer models and I would reccomend that everyone switch to an NVidia-based brand.  They actually care about getting the job done right and the performance of their cards blows ATI clean away long before either company's drivers come in - at which point NVidia wins again.

If you're going Windows or Linux, go NVidia.  That's my CAD2c.

---

### Post by parsons151185 on 2006-08-18
the new drivers released today work perfectly, just got to wait for a deb to install them without having to recompile the kernel very time there is an update

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually)


I'd rather you didn't flame us ATI users, it is entirely personal preference as to what you choose to use, if you cant be civil go else where.

Oh thought I'd just add this in responce to SniperSlap
My friend bought a Compaq which included a NV FX 5200...your telling me they are state of the art? LOL, it couldnt even display bic videos properly, loading DoW took so long because he'd get 1-2 FPS the fix my old Radeon 9600Pro hes had no problems ever since, we runs Windows XP SP2. I never found the problem why it did that, wouldnt boot on my Athlon 3200+ when the FSB was set to 400, its now sat in my old P3-800 system running Ubuntu 6.06 Server

---

### Post by YumaJim on 2006-08-23
I had to save the target as Josh noted in order to download the
posted fix.

Josh - I see your posted file has an '.htm' extension.
I think if you remove the '.htm' it will make it easier
for users to download. When I first clicked on it my browser
it displayed as bunch of garbage.

Will try this fix later and let you know if it works,
sure hope so.

---

### Post by juanc_martinez on 2006-08-26
Hi, I replaced the file and everything worked fine for a while and suddenly the bug started again and now the file replacement procedure doesn't fix it, any idea ?

Sorry. I didn't notice my problem was already discussed on the thread: The problem was the link to the old library copy.

---

### Post by jconcepcion on 2006-08-29
I copied the file on this post and it also fixed my issue as well.

---

### Post by Wolf359T on 2006-09-18
Woked here too, but when I preview some OpenGL screenssaver, the image flickers...

---

### Post by _Dan on 2006-09-20
Just out of interest, when is this problem going to be fixed?

At this rate i'm going to have to disable updates when I go away so it doesn't "update" fxgl or whatever, breaking openoffice for my mother.

Can't the x.org gl (or whatever...) be removed from updates?

---

### Post by zoram on 2006-10-03
> **juanc_martinez said:**
> Hi, I replaced the file and everything worked fine for a while and suddenly the bug started again and now the file replacement procedure doesn't fix it, any idea ?

Sorry. I didn't notice my problem was already discussed on the thread: The problem was the link to the old library copy.

Same here. 
Can't fix the problem anymore. I could do without the 3d rendering, but I need Open Office !](*,) ](*,)

---

### Post by Mojodog on 2006-10-05
Thanks for the post...this work perfectly! :)

---

### Post by ebbot on 2006-10-06
Thanks a lot for your magic file, it worked great on my machine!
ebbot@c184-13: ~ > fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)

ebbot@c184-13: ~ > glxgears -printfps
5517 frames in 5.0 seconds = 1103.335 FPS
5484 frames in 5.0 seconds = 1096.781 FPS
ebbot@c184-13: ~ > lsmod | grep agp
intel_agp              24700  1
agpgart                36784  2 fglrx,intel_agp
ebbot@c184-13: ~ > glxinfo | grep -i direct
direct rendering: Yes :) 
But it's a pretty lousy FPS:evil: The stock radeon driver gives ~1000
in glxgears. Are there any secret options for xorg.conf?!?
Checked my xorg log and saw this:
	warning	fglrx(0): Option "AGPMode" is not used
Is the AGP running at 1x now, or what?!

---

### Post by CommonMyna on 2006-11-20
In this case I have tried to show very carefully what I did, because I found that a symbolic link file screwed up and it would be very very hard to tell without looking inside the file. Completely above my head why this could happen. I am guessing this could totally throw people off. Anyway see what you think.

Thanks to JetTheHead as his contribution accidentally helped me.  I do not normally come here but I think the forum and thread deserves to know what I found and somebody else more knowleagdable can try and figure out what is going on.

---------------------------------

I have been searching many forum items trying to get fglrx installed properly on Mepis 6.0, I studied my xorg.conf and the Xorg.0.log and to the best of my understanding the the system ought to have worked. In response to fglrxinfo I continued to get something like this:

[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS 
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI

The whole output was 320 lines long. I was getting a bit desperate and despite being a releative new to working consistently with Linux/Mepis 6 I had seen many references to libGL.so.1.2 saving the day.  When I came back to this thread for the 3rd time I looked really carefully and compared with my own system.

I downloaded the lib file and searched my own system and found there was only one active instance. 
/usr/lib/libGL.so.1.2

I saved the 'original' very carefully, also moved it to another folder. I checked that the symbolic link did point to the new file.

root@1[Gert]# ls -la /usr/lib/libGL.so.1*
lrwxrwxrwx 1 root root      12 2006-11-17 12:47 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 Gert users 635084 2006-11-20 00:32 /usr/lib/libGL.so.1.2
root@1[Gert]#

When I checked: 

Gert@1[~]$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Now the Mesa means it is not right yet. I had noticed that in my folder 

/usr/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/lib/fglrx/libGL.so.1.xlibmesa

I renamed the libGL.so.1.2 and I noticed that symbolic link was pointing correctly 
libGL.so.1.xlibmesa -> ../libGL.so.1.2  

I had noticed that JedTheHead on page 9 in forum thread here, failed to have success, so I was not really surprised that I still saw the "Mesa.." message in respons to fglrxinfo.

As I was using Midnight Commander at the time to look at my file structure, I had seen that the file :
libGL.so.1.xlibmesa (pointing correctly to libGL.so.1.2) had a file size of 12 bytes

Linux reports the same:
lrwxrwxrwx 1 root root     12 2006-07-18 09:27 /usr/lib/fglrx/libGL.so.1.2.xlibmesa -> ../libGL.so.1.2
[COLOR="DeepSkyBlue"]
It was shear luck that I decided via MC to have a look inside the link file, and I almost went cross eyed, instead of a few words in Eenglish I was obviously looking at a 'exe' file.

I looked at the file with Konqeror which reported 620 kB size?? What on earth was/is going on??? This was going way beyond what I understand about Linux.  

I decided that first of all the Symbolic link had to be set right, no point in carrying on with the wrong link. [/COLOR]

The coloured I now believe is unimportant, ie there is a behaviour that I don't quite understand but the link files I now consider fine until I find otherewise.



cd /usr/lib/fglrx	; just to make sure that I am in the fglrx folder, yea and notice I am root:

root@1[fglrx]# ln -s libGL.so.1.2 libGL.so.1

When I looked in the libGL.so.1 link file I was greeted with 
"File libGL.so.1: symbilic link to  'libGL.so.1.2'

Now looking at the response to fglrxinfo:

root@1[fglrx]# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)

I had been seeking this message for a very very long time.

glxgears -printfps

root@1[fglrx]# glxgears -printfps
6868 frames in 5.0 seconds = 1373.442 FPS
6848 frames in 5.0 seconds = 1369.574 FPS
6722 frames in 5.0 seconds = 1344.214 FPS
6821 frames in 5.0 seconds = 1364.144 FPS
6827 frames in 5.0 seconds = 1365.209 FPS
6828 frames in 5.0 seconds = 1365.517 FPS

I had never got more than abour 200fps, when using the Mesa driver. This at least told me that I had 3D working.

Below is the 3 last lines that JedTheHead reported, now I am wondering if he may have had the same problem, the Symbolic Link File is not what it perhaps ought to be. We can not tell from the 15 bytes, the size of the file could be 1 Mb, this has really stunned me.

Is it possible that symbolic link files are cameleons?  It is beyond me.

lrwxrwxrwx 1 root root     15 2006-07-18 09:27 /usr/lib/fglrx/libGL.so.1.2.xlibmesa -> ../libGL.so.1.2
-rw-r--r-- 1 root root 410880 2006-06-28 15:21 /usr/lib/fglrx/libGL.so.1.2.xlibmesa.bak
lrwxrwxrwx 1 root root     15 2006-07-05 13:05 /usr/lib/fglrx/libGL.so.1.xlibmesa -> ../libGL.so.1.2

------------------------------------

Mepis 6 has a game TuxCart (3D) and that works fine too. I am not totally happy with the speed of the Radeon 9250 I use but I will look into this now that I believe I may have the driver install under control. Finger Crossed.

You may have noticed that I have done all this as root, all looked really promissing.

Then I rebooted to find I was back to square one, well almost. 

Gert@1[~]$ fglrxinfo
libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

The Mesa is back, libGL error, answer to the problem is not that difficult as two things shows. 

1.. No longer operating as root
2.. Operation not permitted, not saying it can't be carried out.

Problem with permissions. In my case it has been fixed with installing following in my xorg.conf, where it was missing.

    Section "DRI"
         Group        0
         Mode         0666
     EndSection

Something about allowing X to give normal user rwx permission. Ineed to read more about all this.


Gert@4[~]$ glxgears -printfps
6797 frames in 5.0 seconds = 1359.368 FPS
6842 frames in 5.0 seconds = 1368.383 FPS
Gert@4[~]$

The normal user is back in buisness again.

---

### Post by CommonMyna on 2006-11-23
Some further investigation into what symlinks are, made me decide that the idea of having multiple copies of a file should not be necessary.

libGL.so.1.2 appears twice in my case
/usr/lib/       and
/usr/lib/fglrx/

I decided to try a test, I selected /usr/lib/fglrx/ as the folder where the the only file should reside now:

/usr/lib/fglrx/libGL.so.1.2 

is the setup I removed the copy in /usr/lib and place a symbolic link here instead which points to above file.

/usr/lib/libGL.so.1 

The glxgears still work just fine, and my tuxkart game.

---

### Post by tonyshangrila on 2006-12-13
Awesome.  This also fixed the exact same problem that I was having with Wine.

---

### Post by chanls on 2007-01-23
I get around this problem by setting the environment variable "SAL_NOOPENGL=true" such that OpenOffice does not use OpenGL.  I can live with this for now, at least only OpenOffice is the only application I have problem with fglrx so far!


Nelson Chan

---

### Post by joshrobinson on 2007-03-06
31,989 hits on that file i hosted on my domain ground-impact.com
holy crap!

---

### Post by borissjroetskov on 2007-03-25
i had the same prob as almost everyone i think: i used the guide [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") to install the ati binary drivers on my ubuntu dapper. It seemed to work at first sight, but when i used fglrxinfo it showed multiple lines saying:
> [fglrx] API ERROR: could not register entrypoint for...
so i googled and came across this forum.

After replacing my libgl.so.1.2 with the one i downloaded, my ubuntu fails to boot: i can still get the logon screen, but after typing in my username and password, the screen flashes one time, and i get a blank screen with brown background and my mouse pointer. I can still move the mouse pointer but nothing seems to happen, even after quite a long time. I tried to undo the action by replacing the libgl.so.1.2 from the ubuntu install disk, but i still have the same problem. Even when i replace my xorg.conf with an older one, the problem persists.

can anyone pls help me?

---

### Post by garion on 2007-04-20
It took me quite a while to figure it out, and this may apply to yours and some people's case in this thread.  Open office conflicts with the combination of "fglrx + scim input", weird hah, but that's what it is... took me forever to find out.  The symptom is that openoffice works with "SAL_NOOPENGL=true" or open source driver, but not fglrx.  My solution was to install scim-bridge agent and client, and change the env variable of GTK_IM_MODULE to scim-bridge instead of scim... then voila problem solved.  Give it a try.




> **chanls said:**
> I get around this problem by setting the environment variable "SAL_NOOPENGL=true" such that OpenOffice does not use OpenGL.  I can live with this for now, at least only OpenOffice is the only application I have problem with fglrx so far!


Nelson Chan

---

### Post by -=Ghostlike=- on 2007-04-21
Hi, I'm a bit stupid, but I don't know how to set these environment variables, when I do export GTK_IM_MODULE=scim-bridge it only stores it in that terminal window and sudo export gives a command not found

Thanks, Casper

---

### Post by borissjroetskov on 2007-04-21
hi there

i had the same problem as almost everybody here: a long list of [fglrxinfo] API ERROR: could not register....

i googled and came across this page, and off course i used the solution. the first time i used it, i got a serious error: i couldn't get past my logon screen. Now, a few weeks later, i had the same problem with my new installation, and after backing-up my ubuntu (with ghost) i tried this solution and it worked :) 
but again, a few hours and a wine-installation later, the drivers fail to work :( 

i already tried replacing the old libGL.so.1.2 (the one i downloaded) with the original (from a backup) but the problem is still there). I also tried al the hints from the binarydriverhowto/ati page troubleshoot section, but nothong seems to work

can anyone pls help? thx in advance

---

### Post by borissjroetskov on 2007-04-23
a few hours ago i ghosted my pc to a previous state (a decently working ubuntu)
i installed the ati drivers, confirmed they worked (with fglrxinfo and by playing warsow)

and guess what? a few reboots later ... the drivers fail. (the same API errors with fglrxinfo)
even when i repeat all the steps from the binarydriverhowto/ati and recopy the libGL.so.1.2, the drivers fail to load.

---

