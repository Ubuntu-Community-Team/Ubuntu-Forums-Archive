---
title: "Google Earth 4.1 + Ubuntu 7.04 + Intel 945GM"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by FerhatBingol on 2007-05-31
I am posting this question here because I believe it is a video driver problem

I setup Google Earth 4.1 for linux to my ubuntu box and if I try to run it it crashes the XServer.

At directory /opt/google-earth/linux I found drivers.ini file and chop of the part about Intel graphic cards. 

Do you think I am on the right tack? Does any body has any information about this? 

Can the problem be that my current drivers maybe do not support MESA and Google Earth crashes thats why?

TIA

        VENDOR >= Intel {
            SETTINGS {
                manufacturerUrl       = [www.intel.com](www.intel.com)
                manufacturerDriverUrl = support.intel.com/support/graphics

                ; The new Intel chipsets do not support vertex arrays.
                disableVertexArrays = true

                ; NEEDS TESTING - B.B. - 6/26/04
                ; anisotropic filtering is busted on Intel graphics chips
                ; this will turn it off even if the hardware claims to support it
                disableAnisotropicFiltering = true

                ; B.B. - 6/26/04
                ; improve performance for fill polys by limiting quality
                ; e.g. 865 takes ~160ms to copy 1K texture from backbuffer, ~40ms with 512
                Render/fillPolysMaxTex = 512

                ; F.B. - 7/14/04
                ; Most intel chips don't support mipmaps. Only enable if tested.
                ; Symptom of overlays -> white and also unitex (unlike DX)
                enableMipmaps = false

                ; B.B. - 7/14/04
                ; saw one case where OGL drivers go from 15fps to 1fps
                ; using 2k instead of 1k textures, couldn't be reproduced.
                ; Render/maxTextureSize = 1024

                ; B.B. - 9/29/05
                ; confirmed as not working on 865
                Render/fillPolysUseBackBuffer = true
            }

            CHIPSET >= Intel 915 {  ;                                       (PIV northbridge)
                SETTINGS {
            }}
            CHIPSET >= Intel 865 {  ; Intel 865 {G,GV}                      (PIV northbridge)
                SETTINGS {
                    ; B.B. - 6/24/04
                    ; good on the 865G
                    enableMipmaps = true
            }}
            CHIPSET >= Intel 845 {  ; Intel 845G
                SETTINGS {
                    ; B.B. - 7/14/04
                    ; all textures -> white
                    enableMipmaps = false

                    ; B.B. - 9/2/04
                    ; forceSleep causes texturing problems
                    Render/forceSleep = false
            }}
            CHIPSET >= Intel 85 {   ; Intel {GM,i852/855}
                SETTINGS {
            }}
            CHIPSET >= Intel 82 {   ; Intel {GM/GME 825xx}
                SETTINGS {
                    ; F.B. - 7/14/04
                    ; all textures -> white
                    enableMipmaps = false;
            }}
            CHIPSET >= Intel 81 {   ; Intel 815 {CGC, Chipset AGP Bridge}   (PII/PIII northbridge)
                                    ; Intel 810 {,E,DC-100,DC-133,-M}       (PII northbridge)
                SETTINGS {
            }}
        }

---

### Post by crispy_420 on 2007-06-02
I think google earth need opengl support or some sort of 3D acceleration.

---

