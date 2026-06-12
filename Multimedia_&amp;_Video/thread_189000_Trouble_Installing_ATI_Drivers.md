---
title: "Trouble Installing ATI Drivers"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by jhorner on 2006-06-04
Hello, 

I have had quite a time trying to install the ATI drivers for my 9000 pro.  I even formatted and reinstalled dapper to see if that would resolve it, but I am still getting the same error message.  I followed the instructions from [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").

Here is the output I get when I run fglrxinfo 
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

And this is the output when I run " dmesg | grep fglrx "
```
[4294698.663000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294698.667000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294698.667000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294700.307000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294700.307000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294700.307000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4294700.308000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294700.322000] [fglrx] total      GART = 134217728
[4294700.322000] [fglrx] free       GART = 118222848
[4294700.322000] [fglrx] max single GART = 118222848
[4294700.322000] [fglrx] total      LFB  = 124436480
[4294700.322000] [fglrx] free       LFB  = 109076480
[4294700.322000] [fglrx] max single LFB  = 109076480
[4294700.322000] [fglrx] total      Inv  = 0
[4294700.322000] [fglrx] free       Inv  = 0
[4294700.322000] [fglrx] max single Inv  = 0
[4294700.322000] [fglrx] total      TIM  = 0

```

Any suggestions??

---

### Post by gumbald on 2006-06-04
I'm having the same problems, no other thread has fixed me yet! Can anyone give a definitive guide?

I've got a Radeon 9200SE.

---

### Post by RavenOfOdin on 2006-06-04
[QUOTE=gumbald]
I've got a Radeon 9200SE.[/QUOTE]

Ditto.

---

### Post by jhorner on 2006-06-04
Well, atleast I am not alone in my troubles.  Just for reference, to my recollection, I was able to install in Breezy.

---

### Post by jhorner on 2006-06-04
Just for clarification, has anyone with this problem tried the second method?

---

### Post by phrstbrn on 2006-06-05
I'm having the same problem.  I have an ATI Radeon 9200 (non-SE).  I used a fresh install of dapper, and also followed the instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") and used Method 1

fglrxinfo
```
zford@zfdesktop:~$ fglrxinfo
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

dmesg | grep fglrx```

zford@zfdesktop:~$ dmesg | grep fglrx
[4294706.143000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294706.146000] [fglrx] Maximum main memory to use for locked dma buffers: 1412 MBytes.
[4294706.147000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294707.153000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294707.154000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294707.154000] [fglrx] AGP detected, AgpState   = 0x1f004e1b (hardware caps of chipset)
[4294707.155000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4294707.168000] [fglrx] total      GART = 67108864
[4294707.168000] [fglrx] free       GART = 51113984
[4294707.168000] [fglrx] max single GART = 51113984
[4294707.168000] [fglrx] total      LFB  = 126873600
[4294707.168000] [fglrx] free       LFB  = 116387840
[4294707.168000] [fglrx] max single LFB  = 116387840
[4294707.168000] [fglrx] total      Inv  = 0
[4294707.168000] [fglrx] free       Inv  = 0
[4294707.168000] [fglrx] max single Inv  = 0
[4294707.168000] [fglrx] total      TIM  = 0

```

---

### Post by larryni on 2006-06-05
Same problem here with my Radeon 9250.

[QUOTE=jhorner]Just for clarification, has anyone with this problem tried the second method?[/QUOTE]
Yes, I've tried both - several times - with the same results.

---

### Post by achilleus78 on 2006-06-05
I'm having exactly the same problems with my 9200SE :(. Hope somebody finds a way to have those drivers work.

---

### Post by richbarna on 2006-06-05
Any Help ? :-
[http://tonywhitmore.co.uk/blog/index.php?id=92]("http://tonywhitmore.co.uk/blog/index.php?id=92")
[http://xoomer.alice.it/flavio.stanchina/debian/fglrx-installer.html]("http://xoomer.alice.it/flavio.stanchina/debian/fglrx-installer.html")

Would it not be possible to install the old ATI drivers that worked ?
[http://packages.ubuntulinux.org/hoary/misc/xorg-driver-fglrx]("http://packages.ubuntulinux.org/hoary/misc/xorg-driver-fglrx")

Sorry guys, just searching around for suggestions.
I use nVidia, so can't give any personal info.

---

### Post by jhorner on 2006-06-05
Would the old drivers allow me to use XGL and Compiz?

---

### Post by japs_it88 on 2006-06-05
I tried a few times to install flgrx drivers and reconfiguring xorg.conf file, but i didn't succed in enabling 3Dacceleration support, nor in making the fglrxinfo returned ATI instead of mesa.

i reinstalled linux ati drivers, which seem to support a pretty good 3Dacc. Using  glxgears -printfps i got:
3175 frames in 5.0 seconds = 634.997 FPS

It is not bad for my radeon 9200 SE.
I think it is better to go back to linux drivers until someone will figure out where's the trick.

---

### Post by jhorner on 2006-06-05
Do you have any idea (or is there a guide) to revert all of the steps that I have done previously and how to install the linux ati drivers?? 

also, do these drivers allow you to use XGL and Compiz?

---

### Post by JGKC9AYC on 2006-06-05
I just followed the instructions from [here]("http://ubuntuforums.org/showthread.php?t=143283&page=12") & got this result:

[I]sudo aptitude remove linux-restricted-modules-2.6.15-23-386
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  linux-restricted-modules-386
The following packages will be REMOVED:
  linux-restricted-modules-2.6.15-23-386
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 22.1MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-386: Depends: linux-restricted-modules-2.6.15-23-386 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-386
linux-restricted-modules-386

Score is -652

Accept this solution? [Y/n/q/?]
[/I]
 
I'm a little skittish to go any further because earlier I followed the instructions at the bottom of the page [here]("http://www.ubuntuforums.org/showthread.php?t=186389") & had the following programs removed:

[I]akregator ark arts artsbuilder flac gqview graveman gtk2-engines-gtk-qt
  gtk2-engines-xfce gwenview ivman k3b kappfinder karm katapult kate
  kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings
  kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins
  kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdeprint kdm khelpcenter kio-apt
  kio-locate kitchensync klaptopdaemon klipper kmenuedit kmilo kmix
  knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins konserve kontact konversation kooka kopete korganizer
  kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb krita kscd
  kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksvg ksysguard
  ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings
  kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager
  kwifimanager libcdio3 libdbh1.0-1 libgadu3 libgnokii2 libid3tag0
  libiso9660-3 libkipi0 libkpimexchange1 libkscan1 liblockdev1 liboggflac3
  libpoppler0c2-qt libpythonize0 libsamplerate0 libvcdinfo0 libxine1c2
  metamail mousepad ncompress ocrad poster psutils python-kde3
  python-opengl python2.4-dev python2.4-kde3 python2.4-opengl qca-tls qobex
  rox-filer sox speedcrunch sylpheed sylpheed-claws-scripts sylpheed-i18n
  vcdimager vorbis-tools xfce4 xfce4-appfinder xfce4-artwork
  xfce4-battery-plugin xfce4-clipman-plugin xfce4-diskperf-plugin
  xfce4-fsguard-plugin xfce4-genmon-plugin xfce4-goodies xfce4-icon-theme
  xfce4-minicmd-plugin xfce4-netload-plugin xfce4-sensors-plugin
  xfce4-session xfce4-systemload-plugin xfce4-taskmanager
  xfce4-trigger-launcher xfce4-utils xfce4-wavelan-plugin
  xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xffm4 xfmedia xfprint4
  xine-ui xubuntu-artwork-usplash zoo
[/I]

Can anyone help?

---

### Post by japs_it88 on 2006-06-05
[QUOTE=jhorner]Do you have any idea (or is there a guide) to revert all of the steps that I have done previously and how to install the linux ati drivers?? 
also, do these drivers allow you to use XGL and Compiz?[/QUOTE]

to revert it should be sufficent to remove the package xorg-driver-fglrx from synaptics and then from terminal:

sudo dpkg-reconfigure xserver-xorg

chosing ati instead of fglrx (that should not appear anyways, sicne we removed it)

If you have kept a backup of the /etc/x11/xorg.conf file you can simply replace it to the original one.

I don't know the answer to the second question, i'm a newbie :)

---

### Post by jhorner on 2006-06-05
[QUOTE=japs_it88]If you have kept a backup of the /etc/x11/xorg.conf file you can simply replace it to the original one.
[/QUOTE]

That would have been the smart thing to do.  ](*,) 


Thanks for the advice.

---

### Post by benvdh on 2006-06-05
Hey,

I'm having the same problem here. Did a search on rage3d and found a link in the unofficial ati-drivers bugzilla :

[http://ati.cchtml.com/show_bug.cgi?id=373](http://ati.cchtml.com/show_bug.cgi?id=373)

Their you will probably find the most recent information on the bug,

Regards,

Ben

---

### Post by bosonflux on 2006-06-05
I'm in the same boat. I've tried fresh install, all tips and methods. Radeon 9000 Pro AIW is a "no go". It was working great up to the last couple of updates before the release candidate. Worked great in Breezy also.

---

### Post by JGKC9AYC on 2006-06-06
After I restarted my machine with the changes I posted earlier, it now comes up to a blank screen.
I haven't tried to boot into "safe" mode or whatever that's called.
It seems my XP has a virus (go figure) where it shuts down as soon as the desktop comes up so i'm having to use the wife's machine.  
Can anyone help?  
Thanks!

---

### Post by Vincent_Lin on 2006-06-06
Hi,

I was doing method 2 - compile kernel-source for fglrx, but I was stopped by the fact that Makefile is not there.


vincent@ubuntu42:/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x$ ls -l
&#32317;&#35336; 0
-rw-r--r-- 1 root root  0 2006-06-07 07:47 cc-sanity-check
-rw-r--r-- 1 root root  0 2006-06-07 07:47 gcc-check
lrwxrwxrwx 1 root root 15 2006-06-07 07:47 Makefile -> Makefile.kbuild
vincent@ubuntu42:/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x$

What ls -l says here is that Makefile is linked to Makefile.kbuild, but Makefile.kbuild is actually not there.  So, compilation stopped.

Help!

Vincent
IBM T42 with ATi 9600m, xunbuntu desktop

---

### Post by JGKC9AYC on 2006-06-06
Anyone?

---

### Post by CzarDerivative on 2006-06-06
Um... yeah. So +1 for the list of users with this exact problem. I first did an upgrade from Breezy to Dapper (with the update manager), and noticed that direct rendering stopped working. I reinstalled from scratch, and things *seemed* to be working, except I got a weird crash the first time it loaded a 3d screensaver. That, and a lot of the buttons in GTK apps were showing up in weird colors (red, yellow, black with unreadable text) until you moused over them. I followed instructions on [this]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI") page, and then started getting the same errors glxinfo, fglrxinfo, etc... and 3d completely stopped working (not even software rendering). 

Now I'm stuck. I'll probably reinstall anyway, since I just installed a few hours ago and there's really nothing new on this system... but I'd like to see some sort of fix to this problem. 

Does anyone know anything about the funny GTK button colors? I strongly suspect it's a rendering issue, but maybe it's something with the new theme?

---

### Post by JGKC9AYC on 2006-06-06
I just wanna know what I can do to see my frickin' login screen so I can try & fix this issue w/o reinstalling (although i'm downloading the 64 bit version on my wife's machine as I type this).

---

### Post by jhorner on 2006-06-07
[QUOTE=JGKC9AYC]I just wanna know what I can do to see my frickin' login screen so I can try & fix this issue w/o reinstalling (although i'm downloading the 64 bit version on my wife's machine as I type this).[/QUOTE]

can you boot into command prompt??  if so try 

```
sudo dpkg-reconfigure xserver-xorg
```

These are the instructions from [this page]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").

It should revert back to the original Xorg driver.

Just for the record, I wish someone would atleast shed some light on this issue.  As to why it may be happening??

---

### Post by Ivhassel on 2006-06-07
[QUOTE=JGKC9AYC]I just wanna know what I can do to see my frickin' login screen so I can try & fix this issue w/o reinstalling.[/QUOTE]

Reinstalling your system = the windows way of solving things
Fixing & reconfiguring = the way to go.

That said, give this a shot:

```

sudo gedit /etc/X11/xorg.conf 
## for kubuntu users, you might want to use nano instead of gedit

Go to the section "device"
the driver probably says "fglrx" which is the 3D accelerated driver. 
Since that one is messed up, change the driver to "ati" for now.

ctrl + X to quit, and don't forget to save.

Now start your Gnome / KDE:
gnome-session

Normally the login screen should appear.

```

That should help you.

---

### Post by gumbald on 2006-06-07
Just got glxgears working with one of the file replacement solutions. It then did updates and it's stopped again. I've tried replacing the file in the same way, but nothing. It's starting to annoy me now, might be NVidia time!

---

### Post by Ivhassel on 2006-06-07
Now for those that can't get their fglrx driver working.

```
lspci | grep ATI
```

Will give you something like : 
0000:01:00.0 VGA compatible controller: ATI Technologies Inc **Radeon R250** Lf [FireGL 9000] (rev 02).

That's my graphics card, and that's one of those graphics cards that does not work with the latest, not so greatest ATI driver. The solution is easy:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
Method 2 is what we need, BUT, we're install the previous version of the driver.

Here's how: 
-taken from the link mentioned, but adapted for the previous driver; 
-basically I changed some filenames, so it installs the previous version, not the latest
-this will still show you 2 updates present, for fglrx, and fglrx-control, if i'm not mistaken. If you upgrade those packages, your X-server will be broken again, so don't! If you want to find out how to prevent updating, open konqueror and type "man:apt_preferences" in the location bar.

[SIZE="5"]**Generating/Installing Ubuntu packages for the 8.25.18 drivers in Ubuntu Dapper Manually**[/SIZE]

Important Change: Installation of this driver no longer requires removing the linux-restricted-modules package in order to work. There is a new blacklist feature in Ubuntu Dapper that you can use to go around this.

Blacklist old fglrx module from linux-restricted-modules

```
sudo gedit /etc/default/linux-restricted-modules-common
```

DISABLED_MODULES to include fglrx
File: /etc/default/linux-restricted-modules-common

DISABLED_MODULES="fglrx"


**Installing the new driver**

Download the ATI driver installer: [32bit Installer]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run")

This guide refers to the 32bit version of the driver. If you are using a x86_64 System you need the 64bit Installer. The installation procedure should be the same as for 32bit, except some filenames will differ slightly.

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

*Install necessary tools:*

```
sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```

*Create .deb packages:*

```
chmod +x ati-driver-installer-8.24.8-x86.run
./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper

```

*Install .deb packages:*

```
sudo dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb
sudo dpkg -i fglrx-control_8.24.8-1_i386.deb
```

*Remove any old fglrx deb's from /usr/src/:*

```
sudo rm /usr/src/fglrx-kernel*.deb
```

*Compile the kernel module:*

```
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx
sudo depmod
```

Note: You have to recompile the kernel module after each kernel update!

*Update the xorg.conf file:*

```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Reboot.

**Confirm that it worked**

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```


Please, post here if it works (those that come after you, might find that helpfull, ask here if it doesn't.

---

### Post by JGKC9AYC on 2006-06-07
[QUOTE=jhorner]can you boot into command prompt??  if so try 

```
sudo dpkg-reconfigure xserver-xorg
```

These are the instructions from [this page]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").

It should revert back to the original Xorg driver.

Just for the record, I wish someone would atleast shed some light on this issue.  As to why it may be happening??[/QUOTE]

Yes, I got into the command prompt via recovery mode.  I typed in ```
sudo dpkg-reconfigure xserver-xorg
``` & got the following message:

*Package xserver-org is not installed and no info is available*

Any more ideas/suggestions before I wipe it out?

---

### Post by juicemansam on 2006-06-07
I've quickly read through this thread, so I might be restating a few things. Here's my story. I had my system with kernel 2.6.16.12 and fglrx 8.24.8. I then tried upgraded the kernel to 2.6.16.19 (or 18 ), about a week before fglrx 8.25.18 came out. Everything worked just fine. As soon as fglrx 8.25.18 came out I got excited and installed it (rpm version using alien, as I always did). Everything broke, but I'm used to that. A few days later I upgraded my CPU/Motherboard, but everything, was still broken. I tried many kernel and fglrx version, but nothing worked. So I then put back my older cpu/mobo, but nothing worked (X/fglrx-wise). At this point I was still trying the latest kernel at the time, 2.6.16.19, and both the new fglrx and the previous release. As a last ditch effort to get my UT2004 working again, I downgraded the kernel to what I was last using, 2.6.16.12, and downgraded fglrx to 8.24.8. Everything worked just fine. I did a bit of testing and have a few assumptions about the problem: something was changed after kernel version 2.6.16.12 (or possibly a few version later) that fglrx expected to find but didn't (similar to a failed XP SP2 install, were you get failed entrypoints, and have to uninstall SP2). Until ATI uses the latest kernel as development reference (or adds some ifdefs), we'll have to continue using older, and compatible versions.

Just so you know, I too was getting error in kernel context 0 errors (or something like that), then a working fglrx, but ERROR with regards to entrypoints, and various other errors.

---

### Post by campnic on 2006-06-07
Well, I have more info.  I don't know if it will be useful or not but I'm new, so bear with me:

I did a lspci | grep ATI and found:
0000:05:00.0 VGA compatible controller: ATI Technologies Inc:  Unknown device 7100
0000:05:00.0 VGA compatible controller: ATI Technologies Inc:  Unknown device 7120

I'm trying to use an ATI 1800xt with my Dell 2100fp

I also have a bunc of "Open failed" and "open result is -1" in my xorg.0.log file and a stack trace at the bottom saying it caught a signal 11 (which might have been me hiting alt+ctrl+del a couple times)  I can do any digging around you guys want if you let me know what to try.

---

### Post by AleXit on 2006-06-08
Same problem with ati mobility 9000 ...

Someone help us, please! :(

---

### Post by danoyoto on 2006-06-08
I have followed the instructions a few post above by Ivhassel and everything seems OK.  How do I figure out what my FPS is?

anyway, I still have a small problem, when I plug in my TV to the VIVO of my Radeon 9200SE, so I can watch moviews I've downloaded, I have to reboot for Ubuntu to know there is a new device attached to the video card.  Then, when the system comes up the TV video looks good, the TV is too small for the actual resolution, and the output on the monitor is WAYYYY  bad!!  Seems that the settings for the Monitor are the settings for the TV so the monitor is too bright and the colours are all messed up!  any idea?

---

### Post by Vincent_Lin on 2006-06-08
Has anyone seen this?  

[http://ubuntuforums.org/showthread.php?t=191944](http://ubuntuforums.org/showthread.php?t=191944)

Could someone confirm that it actually works?

I might just try it out myself, if I find some time this afternoon.

Vincent

---

### Post by Tourmaline on 2006-06-08
Thank you very much Ivhassel. I have been around many solutions to get those damn ATI drivers working after upgrading from Ubuntu 5.10 to 6.06 (with ATI drivers or Xorg drivers) without any success, but your solution by using the previous 8.24.8 ATI drivers simply works great ! I am using Ubuntu 6.06 (after using 5.04 and 5.10 since 1 year) on an Acer 803LMI with a Radeon Mobility 9000 (R250) and like many peoples, I had troubles with 3D acceleration using either latest ATI or Xorg drivers witch seems does not support the "old" R2xx gpu series... What a shame from ATI ! Fortunately there is people like you to come up with a 100% working solution. Thanks again.

---

### Post by Ivhassel on 2006-06-08
[QUOTE=danoyoto]I have followed the instructions a few post above by Ivhassel and everything seems OK.  How do I figure out what my FPS is?[/QUOTE]

open a terminal & type
```

glxgears -printfps

```

[QUOTE=danoyoto]
anyway, I still have a small problem, when I plug in my TV to the VIVO of my Radeon 9200SE, so I can watch moviews I've downloaded, I have to reboot for Ubuntu to know there is a new device attached to the video card.  Then, when the system comes up the TV video looks good, the TV is too small for the actual resolution, and the output on the monitor is WAYYYY  bad!!  Seems that the settings for the Monitor are the settings for the TV so the monitor is too bright and the colours are all messed up!  any idea?[/QUOTE]

I haven't used my TV out on this card, under linux, so I'm afraid I can't help you here.
If you find out how to fix it, please post it. :)

[QUOTE=Tourmaline]Thank you very much Ivhassel. I have been around many solutions to get those damn ATI drivers working after upgrading from Ubuntu 5.10 to 6.06 (with ATI drivers or Xorg drivers) without any success, but your solution by using the previous 8.24.8 ATI drivers simply works great ! I am using Ubuntu 6.06 (after using 5.04 and 5.10 since 1 year) on an Acer 803LMI with a Radeon Mobility 9000 (R250) and like many peoples, I had troubles with 3D acceleration using either latest ATI or Xorg drivers witch seems does not support the "old" R2xx gpu series... What a shame from ATI ! Fortunately there is people like you to come up with a 100% working solution. Thanks again.[/QUOTE]

You're welcome :D

---

### Post by Vincent_Lin on 2006-06-08
Hey Guys,

I have tried the method that I mentioned in my last post.

It works.  Thank you very much.

Based on the procedure, it seems that oss ati driver has left something that prevent fglrx driver to work. 

One thing that I had to change was that xorg.conf actually had two entries for Device, as mentioned somewere else in the forum, and I simply changed one entry with "vesa" into "fglrx".  The other entry was "fglrx" already.

Another matter, totally not related to this thread, was that LiveCD intall has a bug preventing it from finishing instalaliton, when I chose "Traditional Chinese" as my preferred language.  The "third" try using standard "American English" allowed me finish this venture.

So now my dapper with 686 kernel running on T42 with 9600m has accelerated 3D rendering.  Time to xgl/compiz goodies.

Vincent

---

### Post by JGKC9AYC on 2006-06-08
[QUOTE=JGKC9AYC]Yes, I got into the command prompt via recovery mode.  I typed in ```
sudo dpkg-reconfigure xserver-xorg
``` & got the following message:

*Package xserver-org is not installed and no info is available*

Any more ideas/suggestions before I wipe it out?[/QUOTE]

Anyone?

---

### Post by Ivhassel on 2006-06-09
[QUOTE=JGKC9AYC]Anyone?[/QUOTE]

Do you recall removing that package? It should just be there if you didn't ...

If you have a working internet connection, or an (K)ubuntu CD at hand, try:
```

sudo apt-get install xserver-xorg

```

---

### Post by cosine7 on 2006-06-09
Well i tried that... still got the mesa, i have r280 9200 Radeon..... any other sugestions?

---

### Post by cosine7 on 2006-06-09
fglrxinfo = this output

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

### Post by Ivhassel on 2006-06-09
[QUOTE=cosine7]fglrxinfo = this output

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)[/QUOTE]


Please post the following info:
I'll have a look

[LIST]
[*]Output of
```
lspci | grep ATI
```
[*]Output of
```
fglrxinfo
```
[*]Output of
```
glxinfo
```
[*]Your /etc/X11/xorg.conf
[*]What error messages do you get? Possibly this: [fglrx] API ERROR: could not register entrypoint for *$API*
[/LIST]

I might not be able to help, but I can compare it with my working config, or someone else might be able to help, based on your info

---

### Post by baldass_newbie on 2006-06-09
[QUOTE=Ivhassel]Please post the following info:
I'll have a look

[LIST]
[*]Output of
```
lspci | grep ATI
```
[*]Output of
```
fglrxinfo
```
[*]Output of
```
glxinfo
```
[*]Your /etc/X11/xorg.conf
[*]What error messages do you get? Possibly this: [fglrx] API ERROR: could not register entrypoint for *$API*
[/LIST]

I might not be able to help, but I can compare it with my working config, or someone else might be able to help, based on your info[/QUOTE]

Hey, mind if I jump in?  I'm getting the same error.  

```
user@computer:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)

```

```
user@computer:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```


```
user@computer:~$ glxinfo
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

```

And my xorg.conf: 
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
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SONY CPD-E40"
	Option		"DPMS"
	HorizSync	30-96
	VertRefresh	48-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200]"
	Monitor		"SONY CPD-E40"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
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

```

And finally, when I run glxgears:
```
user@computer:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

```

Any and all help is greatly appreciated.
\\:D/

---

### Post by Ivhassel on 2006-06-09
[QUOTE=baldass_newbie]Hey, mind if I jump in?  I'm getting the same error.  

```
user@computer:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc **RV280** [Radeon 9200] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)

```
[/quote]

**RV280** <= that means the fglrx drivers from the repositories will NOT work with this chipset. Check my howto (post #26 in this thread) on how to install the previous ATI drivers.

[QUOTE=baldass_newbie]
And my xorg.conf: 
```

<cut>
Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200]"
**	Driver		"ati"**
	BusID		"PCI:1:0:0"
EndSection
<cut>

```
[/quote]

Once you've followed my howto, then it should say Driver "fglrx" here. Follow the howto to accomplish this.

[QUOTE=baldass_newbie]
Any and all help is greatly appreciated.
\\:D/[/QUOTE]

---

### Post by larryni on 2006-06-09
[QUOTE=Ivhassel]Now for those that can't get their fglrx driver working.

[...]


Please, post here if it works (those that come after you, might find that helpfull, ask here if it doesn't.[/QUOTE]
Thank you so very much! This finally got my graphics sorted \\:D/

---

### Post by cosine7 on 2006-06-09
[QUOTE=Ivhassel]Please post the following info:
I'll have a look

[LIST]
[*]Output of
```
lspci | grep ATI
```
[*]Output of
```
fglrxinfo
```
[*]Output of
```
glxinfo
```
[*]Your /etc/X11/xorg.conf
[*]What error messages do you get? Possibly this: [fglrx] API ERROR: could not register entrypoint for *$API*
[/LIST]

I might not be able to help, but I can compare it with my working config, or someone else might be able to help, based on your info[/QUOTE]
lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5940 (rev 01)

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

glxinfo
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
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"AS4637"
	Option		"DPMS"
	HorizSync	24-80
	VertRefresh	56-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor		"AS4637"
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

---

### Post by Ivhassel on 2006-06-09
> **cosine7]lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5940 (rev 01)
[/QUOTE]
As far as I've read, any chipset = R2xx should use ATI driver. 
As shown by your fglrxinfo, your system runs the generic driver, so if you have the ATI drivers from the Dapper Release now, I'd suggest you try installing the previous ATI drivers, with my howto, somewhere in this thread  said:**
> 
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


---

### Post by cosine7 on 2006-06-09
well, i followed the guide, with no errors, until i reboot, when the screen goes to enter the login page, the screen just goes black. Thinking that had well and truly f$%*ed it i went and did a complete reinstall (i was thinking about it anyway, bigger hdd) any after a clean install this is the first thing i did( the ati #26 walkthrough) with no errors, until i reboot, when it comes to switching over, and once again all i get is a black screen. any  thoughts? maybe i'll get an nVidia :)

---

### Post by cosine7 on 2006-06-09
oh and i cannot get a console open either at this point.....
[B][COLOR="Red"]
HELP!!!!!!!!!!!!![/COLOR][/B]

---

### Post by AceRimmer on 2006-06-10
[QUOTE=jhorner]Hello, 

I have had quite a time trying to install the ATI drivers for my 9000 pro.  I even formatted and reinstalled dapper to see if that would resolve it, but I am still getting the same error message.  I followed the instructions from [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").

Here is the output I get when I run fglrxinfo 
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

And this is the output when I run " dmesg | grep fglrx "
```
[4294698.663000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294698.667000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294698.667000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294700.307000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294700.307000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294700.307000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4294700.308000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294700.322000] [fglrx] total      GART = 134217728
[4294700.322000] [fglrx] free       GART = 118222848
[4294700.322000] [fglrx] max single GART = 118222848
[4294700.322000] [fglrx] total      LFB  = 124436480
[4294700.322000] [fglrx] free       LFB  = 109076480
[4294700.322000] [fglrx] max single LFB  = 109076480
[4294700.322000] [fglrx] total      Inv  = 0
[4294700.322000] [fglrx] free       Inv  = 0
[4294700.322000] [fglrx] max single Inv  = 0
[4294700.322000] [fglrx] total      TIM  = 0

```

Any suggestions??[/QUOTE]


I'm having the exact same problem.

---

### Post by cosine7 on 2006-06-10
Well, a few dpkg-reconfigures later, my still will not boot with fglrx, will not boot the ati, but will make the login noise, but will boot under vesa....

---

### Post by Ivhassel on 2006-06-10
[QUOTE=cosine7]oh and i cannot get a console open either at this point.....
[B][COLOR="Red"]
HELP!!!!!!!!!!!!![/COLOR][/B][/QUOTE]
Hang on, I sleep sometimes ... :)

[QUOTE=cosine7]well, i followed the guide, with no errors, until i reboot, when the screen goes to enter the login page, the screen just goes black. Thinking that had well and truly f$%*ed it i went and did a complete reinstall (i was thinking about it anyway, bigger hdd) any after a clean install this is the first thing i did( the ati #26 walkthrough) with no errors, until i reboot, when it comes to switching over, and once again all i get is a black screen. any  thoughts? maybe i'll get an nVidia :)[/QUOTE]

Reboot into safe mode. You'll end up at a terminal. 
First look in */etc/X11/xorg.conf* what driver you're using, in the driver section. If it says fglrx, change that to vesa for now & save it, so you can boot in gnome/kde.
Then give us some diagnostics again (the 5 bullet list I posted in this thread)

---

### Post by akniss on 2006-06-10
I followed the howto from post 26 of this thread, but got an error during the  ```
sudo ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper
``` 

```

... #prior output deleted for brevity
dh_makeshlibs
dh_installdeb
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/i486-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libstdc++.so.5 not found.
dpkg: /usr/i486-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/i486-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libGL.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libdl.so.2 not found.
dpkg: /usr/i486-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libc.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libgcc_s.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libfglrx_gamma.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libfglrx_pp.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: Leaving directory `/tmp/fglrx'
~/SoftwareInstall/fglrx-install
Removing temporary directory: fglrx-install

```

Why can't I make my .debs?

---

### Post by ranko on 2006-06-10
hi everybody!

i've got a radeon 9600 pro and the fglrx packages in the dapper repositories work fine. my dad, however, has a radeon 9000 pro, so things didn't go as smoothly on the first attempt to install ATI's binary driver. for the second attempt, i did a clean install of dapper and then used lvhassel's HOWTO from this thread (thnx lvhassel!) and it worked, mostly.

as you can see, from the fglrxinfo output pasted below, the fglrx driver seems to be working. however, the framerates for screensavers are really slow, it seems like they're not using fglrx to render (they're the same speed as they were before i installed fglrx). i know how fast they can go because in breezy they were flying, on the same hardware. glxgears gives me 2500 fps, if that helps.

anyway, i'm giving everybody the output from a couple of diagnostic commands suggested by lvhassel, so if anyone has any ideas why my dad's screensavers are slow, it will be much appreciated!

**result from "lspci | grep ATI":**

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)

--------------------------------------------------------------------------------------------------

**result from "fglrxinfo":**

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 PRO DDR Generic
OpenGL version string: 1.3.1060 (X4.3.0-8.24.8)

--------------------------------------------------------------------------------------------------

**result from "glxinfo":**

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 PRO DDR Generic
OpenGL version string: 1.3.1060 (X4.3.0-8.24.8)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_ATI_element_array,
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None

my xorg.conf file is attached in this post.

---

### Post by Ivhassel on 2006-06-10
[QUOTE=ranko]i know how fast they can go because in breezy they were flying, on the same hardware. glxgears gives me 2500 fps, if that helps.
> 

Do you get 2500 fps now ?
That's more or less what I get now, and my card has the same chipset as yours. I can confirm that my 3D is working. I never used Breezy, so I can't compare to that, to see if it feels faster or slower on dapper ...

[QUOTE=ranko]
anyway, i'm giving everybody the output from a couple of diagnostic commands suggested by lvhassel, so if anyone has any ideas why my dad's screensavers are slow, it will be much appreciated!

I see nothing wrong with those *at first sight *

---

### Post by cosine7 on 2006-06-11
with my driver set to ati, i have got it to boot. turns out that DVI does'nt appear to be supported...

---

### Post by ranko on 2006-06-11
[QUOTE=Ivhassel]

Do you get 2500 fps now ?
That's more or less what I get now, and my card has the same chipset as yours. I can confirm that my 3D is working. I never used Breezy, so I can't compare to that, to see if it feels faster or slower on dapper ...



I see nothing wrong with those *at first sight *[/QUOTE]

yeah, glxgears works smoothly, but the 3d screensavers are slow, i think they should be faster on this hardware...
on the atunnel screensaver for example, i'm getting like 4fps (this is just an estimate).
i'll try some game like planetpenguin racer and see how fast it goes.

---

### Post by Ivhassel on 2006-06-11
[QUOTE=cosine7]with my driver set to ati, i have got it to boot. turns out that DVI does'nt appear to be supported...[/QUOTE]

with 
```

sudo dpkg-reconfigure xserver-xorg

```
simply deselect the module "DVI", and use the fglrx driver again. If that's the only thing that kept your fglrx from working, then this should do the trick.

You can always get back to driver "ati", if  it doesn't, so imho (!) it's worth the try.

---

### Post by Ivhassel on 2006-06-11
[QUOTE=ranko]yeah, glxgears works smoothly, but the 3d screensavers are slow, i think they should be faster on this hardware...
on **the atunnel screensaver** for example, i'm getting like 4fps (this is just an estimate).[/QUOTE]

If you tell me how to run that screensaver, while displaying fps, I'll give you my results. As we run the same hardware, I'm particularly interested to see if either of us can get even better performance out of this card.

---

### Post by danoyoto on 2006-06-11
I have the same problem, if I leave the default drivers alone then my FPS in glxgears on fullscreen is like 140-170, when I upgrade to the 8.24 drivers I get the same FPS on glxgears but my screensavers are horrible?  default drivers let the screensavers fly!  I don't get it.......I also want to use my video out to copy my monitor onto my TV but can't figure that out.....at least these minotr annoyances are made up by the fact that this is M$!!!

---

### Post by cosine7 on 2006-06-12
Umm there is no DVI module...

Here is my current situation

VESA Works with anything but slow

ATI works with Anologue but not DVI(with dvi i can hear the login sound, but not see anything)

FGLRX works with nothing, just freezes after ther ubuntu boot sequence

I know this might be odd, but i am running 6.06 x386, but i am using a AMD64 3200+ would this make a difference?

---

### Post by Dr_Deadmeat on 2006-06-12
Try to copy and paste this command and see if it works (it is really many commands merged into one =P)

```

sudo apt-get update && sudo apt-get install module-assistant build-essential && sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base && chmod +x ati-driver-installer-8.24.8-x86.run && ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper && sudo dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb && sudo dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb && sudo dpkg -i fglrx-control_8.24.8-1_i386.deb && sudo rm /usr/src/fglrx-kernel*.deb &&sudo module-assistant prepare,update && sudo module-assistant build,install fglrx && sudo depmod && sudo aticonfig --initial && sudo aticonfig --overlay-type=Xv && sudo /etc/init.d/**gdm** restart

```

you might want to change **gdm** with **kdm** (if you use KDE) or **xdm** (if you use Xfce)

Hope this helps anyone with trouble with this =)

---

### Post by ranko on 2006-06-12
[QUOTE=Ivhassel]If you tell me how to run that screensaver, while displaying fps, I'll give you my results. As we run the same hardware, I'm particularly interested to see if either of us can get even better performance out of this card.[/QUOTE]

i don't know how to see the fps for the screensavers, i was just giving you a visual estimate.

**BUT** i have some good news :-)

i've found a simple solution on another thread, and it seems to be working on my dad's machine with the radeon 9000 pro:

[http://ubuntuforums.org/showthread.php?t=185033]("http://ubuntuforums.org/showthread.php?t=185033")

it boils down to two steps:

1) install the *new* ATI drivers, the ones packaged and included in the dapper repositories. you can use the instructions [here]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI") (from the ubuntu wiki) to do this.
2) replace a single file named /usr/lib/libGL.so.1.2 with the one provided in the above forum thread, one of the people posting (joshrobinson) was great enough to host the file on a server. the file is attached with post #6 in that thread.

anyway, the drivers are installed on my dad's machine, everything seems to be working, and the screensavers are screaming fast :-). also, judging by the responses in that thread, it worked for a lot of people. i hope it works for everybody in this thread too!

also, know that i did a clean install of dapper before doing the above two steps. it probably wasn't neccessary, but i did it just in case.

---

### Post by scarolan on 2006-06-13
lvhassel:

Thank you kindly for posting instructions on how to get OpenGL working.  Unfortunately I followed your instructions to a tee, but I'm still having the MESA problem.  Here are my system specs along with some config files.  I really hope someone can help me get this working.  I am using a Dell D600 Latitude notebook:

scarolan@obiwan:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)

scarolan@obiwan:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

scarolan@obiwan:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32

---

### Post by scarolan on 2006-06-13
Don't know if this part is helpful, but here's some more info from dmesg:

scarolan@obiwan:~$ dmesg | grep fglrx
[4294707.408000] [fglrx] Maximum main memory to use for locked dma buffers: 680 MBytes.
[4294707.408000] [fglrx] module loaded - fglrx 8.24.8 [Apr 11 2006] on minor 0
[4294709.080000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294709.080000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294709.080000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294709.080000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4294709.082000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294709.093000] [fglrx:firegl_unlock] *ERROR* Process 4313 using kernel context 0

---

### Post by Andenium on 2006-06-13
sigh i have to do this but i know nothing of linux so i cant do it my msn is Andenium@hot... if somebody is kind enough to help me i would apreciate it

---

### Post by ACGilbert on 2006-06-21
Thanks Ivhassel. 

The 8.24 drivers are working for me with an ATI 9250, V280 chipset. 
I'm newbie to Linux & Ubuntu. I was ready to give up until I found your post. All in all it was a rewarding exercise.

Don :D

---

### Post by pmshirey on 2006-06-21
> I post this a lot:
Use the soundcard whenever you can
Well atleast I said _WHENEVER_. Yes use the sound card _*whenever*_ you can, And don't be afraid to not use it. I have have had to not use it sometimes. I know it kinda bums all of us terminal geeks. But sometimes you just can't use it. Try using Add/Remove Applications. Good news is you still have a little command line you need to type the file name in.

---

### Post by jgcamp99 on 2006-06-25
The method lvhassel outlined worked without issue initially. However, after the reboot, 2 software updates popped up in the updater:

fglrx-control
fglrx-kernel-source

After updating and subsequent reboot this winds up removing the ATi Control item under Applications.

What's up with that ? Is it somewhere still on the hdd and I have to re-add it again, or does this update remove that altogether ? I like the ATi Control icon and the little application that allows for customizations. But I also like the most up to date system. Can I have both with this ?

BTW, once this ATi driver was installed manually I was able to run the ATi installer for package specific and be able to see all the Ubuntu versions listed.

---

### Post by jgcamp99 on 2006-06-25
Nevermind my last post, I'm slowly fixing those issues. I put an icon on the desktop and panel and then found this to be an issue of the launcher command, so it is still on the hdd and I had to change the command to invoke it:

From:
/usr/bin/fireglcontrolpanel

To:
/usr/bin/fireglcontrol

for the icons. I even was able to change the comments from grafics to Graphics, but that's a preference thing.

Now to add it to the menu trees. And that was as simple as Gnome Alacarte Menu Editor. Used the icon properties to track down everything to be consistent across the board. (System is updated as of this post, 06/25/2006 11:30 PM EST USA).

Radeon 9600 XT 256 MB, Display Driver Version: 8.25.18, OpenGL Version: 2.0.5814

I'm fast becoming an Ubuntu "Ubunut" ! Thanks for the "How To".

---

### Post by Paragon111 on 2006-06-25
lv's walkthrough worked perfect for me and my Radeon 8500. Thanks!

---

### Post by jgcamp99 on 2006-06-26
Just when you finally get 8.25.18 on, 8.26.18 comes out ! The lv walkthru is gold again ! This time it put the ATi Control Panel under Accessories, but I still fixed my menu's and icons to invoke the program. BTW, it also renamed the ATi Control Panel program to:

/usr/bin/fireglcontrolpanel

from:

/usr/bin/fireglcontrol

Once the ATi drivers are on, I noticed the installer fits in the screen @ 1600 X 1200 resolution, but when you go to the package specific item, this installer supports fewer distros from the gui, it even tells you you have to run it  from the command line again with distro specific information. Make sure you see it and write it down. Anyone know, What's the difference between Ubuntu/dapper and Ubuntu 606 ? Then you have to go thru the manual process and it installs/updates to 8.26.18 in the same step by step process. This time, I had to "rm" the old 8.25.18 flgrx and after doing the manual install, the 8.26.18 flgrx was there instead. The reboot did it's job and everything is just wonderful with the newest drivers.

I do this as root, so sudo doesn't apply in the code. It's so much easier that way for me, cut and paste, I even use a text file to edit the driver revision file names and resave it, so I can cut and paste.

---

### Post by JohanSwe on 2006-07-08
> **scarolan said:**
> lvhassel:

Thank you kindly for posting instructions on how to get OpenGL working.  Unfortunately I followed your instructions to a tee, but I'm still having the MESA problem.  Here are my system specs along with some config files.  I really hope someone can help me get this working.  I am using a Dell D600 Latitude notebook:

scarolan@obiwan:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)

scarolan@obiwan:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

scarolan@obiwan:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32

I get the same message as scarolan with the command fglrxinfo.

And I got no direct rendering:
```
johan@johan:~$ glxinfo | grep rendering
direct rendering: No

```

Thanks for the guide anyway. 

I have read in other threads about after ATI driver install getting OpenGL rendering by Mesa. I hope someone can figure out a solution for this.. 

[-o<

---

### Post by jwmislan on 2006-07-08
Why do these people keep buying cards from ATI ?????
All these problems with ATI propriotory drivers are the fault of ati's 
feet dragging with their linux support.

 I bought an ati radeon AIW 7500 back in 2000 or so.
When I saw that ATI was being a jerk about supporting linux, I vowed to
NEVER again buy anything from ATI.
 That is why I still have the old Radeon 7500.
Else I would buy from another vendor, a cheap 3d card that is supported by linux, and also buy a seperate TV card for TV and capture work.

 My Radeon 7500 works fine with the xorg radeon driver. Xawtv works to view
TV, and Composite, but capture is still not working with the xorg radeon driver. I am going to purchase a Plextor ConvertX PVR to use for my capture needs. But I will NEVER Buy ANYTHING from ATI ever again.
 They had more than enough time to get on board with linux to support their product line, and they failed Large !!
 This is really way out of the park, these problems with ati video driver that should JUST WORK. When people are trying to do serious work, and also have some serious Fun, they're getting side-tracked for need to get their new ATI cards Supported - again ATI's fault.
The Linux Kernel developers, and the Xorg People have done their fair share of excellent work. Now how about some of those Lame Vendors try to match it without crying, screamming, and dragging their feet like a bunch of babys.

JWM

---

### Post by Dubbayoo on 2006-07-08
I've had my 8500 since 2002 at least. It wasn't an issue til I started wanting to use *nix full time which was recently.

---

### Post by scarolan on 2006-07-08
I'm in the same boat as jwmislan regarding ATI.  I've always had problems getting OpenGL working with Linux, but every nVidia card I've bought has worked flawlessly under Linux.  

Unfortunately the laptop I'm trying to get working is a company laptop, so I don't have much of a choice there.  At least until it breaks and I can get a new one, I'm stuck with the ATI card.

---

### Post by JohanSwe on 2006-07-09
There is a new driver out at ATI's webpage. Maybe it's working but I can't tell because my OpenGL is rendered by Mesa just like when trying to use the old driver (see post #72).

Yesterday I booted with the ubuntu live cd and changed *ati* in xorg.config to *radeon,* restarded the session (not the computer) and openGL seemed to work just fine.

Now I have screwed up my Ubuntuinstallation when following to many guides, but at a fresh ubuntu install this should work just fine.

---

### Post by coldpost on 2006-07-09
Hi guys I amy be about to sound real dumb. I stumbled across this forum whilst tryin to figure out why my 9200se keeps crashin certain games.

My spec.

P4 2.8
1G ddr ram 133
windows xp
radeon 9200se
dont know motherboard.

Anyway very new to this an im gonna assume its my drivers when i got the PC it took me forever searching for drivers but found some that seemed to work, however the current games that are about keep crashin my system.

The dumb bit is i dont know if you guys are all runnin linux or a variety of OS.

Bottom line is most of you sound much more knowledgable about this stuff than me, so any help with links to current drivers or just general fixes i could try would be great.

oh my current drivers are probably about 1 and a half yrs old (driver version 6.14.10.6490) i think its catalyst.

Please please please help a fellow gamer.

Cheers.

---

### Post by gumbald on 2006-07-09
What OS are you running? Everyone here is (should be) running Ubuntu Linux. If you're having trouble with the latest games, you could have found the limit to your 9200SE, it's not the best graphics card for gaming...

---

### Post by coldpost on 2006-07-09
running windows XP home.

Sorry to sound dim but ive been out of the loop so long im not really up to speed on different OS'.

Dont know if ya can but any ideas where to hit next.

Im tryin to run star wars empire at war, age of empires 3, condemned. that sort of thing they all start but about 30 mins in they just crash.

once again thanks!!!!

---

### Post by Tristan9669 on 2006-07-14
thanks Ivhassel!

---

### Post by sampoerna on 2006-07-14
First of all, GREAT THX to Ivhassel for the post.
now my ATI Radeon 92000SE works on dapper, even better than in breezy.
which i get average 980FPS in breezy, now 1200FPS in dapper :) 

> **coldpost said:**
> Hi guys I amy be about to sound real dumb. I stumbled across this forum whilst tryin to figure out why my 9200se keeps crashin certain games.

My spec.

P4 2.8
1G ddr ram 133
windows xp
radeon 9200se
dont know motherboard.

Cheers.

dear coldpost,
I dont play 3d games on my ubuntu, but just for your information, i can use STELLARIUM(the star simulation program) for hours without problem.

Btw i used the ati-driver-installer-8.24.8-x86.run
and when i tried to 

> 
sudo module-assistant prepare,update


it shows a warning in terminal asking me to use 'apt-get -f update'
by doin that i've update my fglrx-kernel to 2.6.15

After that everything went smooth:rolleyes:

> $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.1060 (X4.3.0-8.24.8)


> $ glxgears -printfps
6087 frames in 5.0 seconds = 1217.231 FPS
6045 frames in 5.0 seconds = 1208.902 FPS
6032 frames in 5.0 seconds = 1206.275 FPS
6057 frames in 5.0 seconds = 1211.316 FPS
6034 frames in 5.0 seconds = 1206.788 FPS
6035 frames in 5.0 seconds = 1206.804 FPS
6018 frames in 5.0 seconds = 1203.443 FPS
6059 frames in 5.0 seconds = 1211.721 FPS


---

### Post by Rippy on 2006-07-14
I have the same problem with my Radeon 9250... I'll have to try ATI's new driver, but every single guide i've tried has failed one way or another..

---

### Post by Darth Tux on 2006-07-27
hey, this is a great howto but i got stuck at the part where it says:

[COLOR="DarkRed"]"sudo module-assistant build,install fglrx"[/COLOR]

All i get is this:
[COLOR="DarkRed"]

dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
cat /usr/src/modules/fglrx/debian/control.template >
/usr/src/modules/fglrx/debian/control; \
i
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \
mv /usr/src/modules/fglrx/debian/postinst
/usr/src/modules/fglrx/debian/fglrx-kernel-2.6.17.7-bob.postinst; \
fi
dh_testdir
touch configure-stamp
dh_testdir /usr/bin/make -C /usr/src/kernel-headers-2.6.17.7-bob SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/kernel-headers-2.6.17.7-bob'
/usr/src/kernel-headers-2.6.17.7-bob/arch/i386/Makefile:38:
/usr/src/kernel-headers-2.6.17.7-bob/arch/i386/Makefile.cpu: No such file or directory
make[1]: *** No rule to make target
/usr/src/kernel-headers-2.6.17.7-bob/arch/i386/Makefile.cpu'. Stop.
make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.7-bob'
make: *** [build] Error 2
^Y[/COLOR]

I did compile a custom kernel though, so that could be part of the problem.  I just don't know how to fix it. 

Thanks for any help,

-darthtux

---

### Post by daone on 2006-08-12
Sigh, I have been trying for weeks to get my ATI 9000 pro working with full 3D support. Everytime I enable fglrx I get no login screen upon reboot.

If I enable ati driver, I can't even get 100 fps with glxgears.

I've tried using the guides in these post and xserver crashes or never starts everytime.

I've been trying these guides on a fresh install of Kubuntu Dapper.

Is there anyone with a definitive guide to get a 9000 pro working fully in Dapper?

---

### Post by andb on 2006-09-04
I've successfully installed an ATI 9250, all the drivers are working. However, if I switch to one of the text terminals (crtl-alt-F1) and then switch back to the x terminal (ctrl-alt-F7) the machine hangs. It will change graphic modes, draws the mouse pointer and hangs until I pull the power. Sometimes the hardrrive light is indicating a lot of activity, other times not. 

Anyone else ever see this problem?

---

### Post by cosine7 on 2006-09-04
Wow, I'm impressed you got the 9250 working at in 3D! I've been trying for 3 months now...

---

### Post by leftwing on 2006-09-05
I have the same problem with a Radeon 9600 Pro. ](*,) 

I don't want to waste time with it anymore. 

Next time I'll but a Nvidia card.

---

### Post by jubilee33 on 2006-09-07
I tried getting some help for ati radeon xpress 200m to no avail.  Please see below.

[http://ubuntuforums.org/showthread.php?p=1472856#post1472856]("http://ubuntuforums.org/showthread.php?p=1472856#post1472856")

My X server doesn't work and I have no working connection.  I am considering trying the second method to install the new ati driver but I don't know how to proceed because I am very new to Ubuntu.  Can anyone teach me how to proceed with no internet connection or is it entirely impossible? ](*,)

---

### Post by Crickster on 2007-03-19
I had a bit of trouble getting my ATI Club 9250 card going on Ubuntu Dapper but this thread worked an absolute treat.
Thanks a million.

---

