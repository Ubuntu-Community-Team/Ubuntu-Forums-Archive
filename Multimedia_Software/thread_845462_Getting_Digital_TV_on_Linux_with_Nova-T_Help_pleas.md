---
title: "Getting Digital TV on Linux with Nova-T? Help please!"
date: 2008-06-30
forum: Multimedia Software
---

### Post by cova on 2008-06-30
I have been given a Hauppauge WinTV Nova-T stick and am wondering how to get it working under linux. I havent a clue where to start. Could anyone help me with some kind of step-by-step guide as to what to do to get this installed? I understand it can run under Kaffeine. Help greatly appreciated! I am running Ubuntu Hardy. Already have Kaffeine and Gstreamer ffmpeg plugin installed (thats about all i could find searching the forums).
Cheers!
Ben

---

### Post by xc3RnbFO8P on 2008-06-30
First in Terminal:
> lsusb
show the output.

---

### Post by cova on 2008-06-30
```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 2040:7070 Hauppauge 
Bus 001 Device 001: ID 0000:0000
```

---

### Post by xc3RnbFO8P on 2008-06-30
1
> sudo apt-get install build-essential
2
> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
3
> cd v4l-dvb
4
> make all
5
> sudo make install
Restart the computer
Open Kaffeine

---

### Post by cova on 2008-06-30
ok done that. Nothing seems to have happened. Is there anything else I need to do?
EDIT: found  the Enable DVB client in Setup Menu and now enabled. NBow clicked DVB client. Now what do I need to do?

---

### Post by xc3RnbFO8P on 2008-06-30
In Terminal:
> dmesg
see if you get dvb-usb-dib0700-1.10.fw loaded.

---

### Post by cova on 2008-06-30
> **Ringi said:**
> 
see if you get dvb-usb-dib0700-1.10.fw loaded.
done the first bit but what do you mean by that?

---

### Post by xc3RnbFO8P on 2008-06-30
Show the output of dmesg.

---

### Post by cova on 2008-06-30
```
[19136.081576] VFS: busy inodes on changed media.
[19138.079101] VFS: busy inodes on changed media.
[19138.080999] VFS: busy inodes on changed media.
[19140.078695] VFS: busy inodes on changed media.
[19140.080579] VFS: busy inodes on changed media.
[19142.078298] VFS: busy inodes on changed media.
[19142.080142] VFS: busy inodes on changed media.
[19144.077887] VFS: busy inodes on changed media.
[19144.079754] VFS: busy inodes on changed media.
[19146.077465] VFS: busy inodes on changed media.
[19146.079321] VFS: busy inodes on changed media.
[19148.077064] VFS: busy inodes on changed media.
[19148.078952] VFS: busy inodes on changed media.
[19150.076684] VFS: busy inodes on changed media.
[19150.078552] VFS: busy inodes on changed media.
[19152.076284] VFS: busy inodes on changed media.
[19152.078157] VFS: busy inodes on changed media.
[19154.075873] VFS: busy inodes on changed media.
[19154.077792] VFS: busy inodes on changed media.
[19156.075552] VFS: busy inodes on changed media.
[19156.077432] VFS: busy inodes on changed media.
[19158.079090] VFS: busy inodes on changed media.
[19158.081057] VFS: busy inodes on changed media.
[19160.074667] VFS: busy inodes on changed media.
[19160.076569] VFS: busy inodes on changed media.
[19162.074454] VFS: busy inodes on changed media.
[19162.076368] VFS: busy inodes on changed media.
[19164.073952] VFS: busy inodes on changed media.
[19164.075820] VFS: busy inodes on changed media.
[19166.073486] VFS: busy inodes on changed media.
[19166.075373] VFS: busy inodes on changed media.
[19168.073202] VFS: busy inodes on changed media.
[19168.075517] VFS: busy inodes on changed media.
[19170.072709] VFS: busy inodes on changed media.
[19170.074594] VFS: busy inodes on changed media.
[19172.072283] VFS: busy inodes on changed media.
[19172.074164] VFS: busy inodes on changed media.
[19174.071882] VFS: busy inodes on changed media.
[19174.073798] VFS: busy inodes on changed media.
[19176.073180] VFS: busy inodes on changed media.
[19176.075175] VFS: busy inodes on changed media.
[19178.071109] VFS: busy inodes on changed media.
[19178.072995] VFS: busy inodes on changed media.
[19180.070667] VFS: busy inodes on changed media.
[19180.072520] VFS: busy inodes on changed media.
[19182.070225] VFS: busy inodes on changed media.
[19182.072100] VFS: busy inodes on changed media.
[19184.069873] VFS: busy inodes on changed media.
[19184.071770] VFS: busy inodes on changed media.
[19186.069466] VFS: busy inodes on changed media.
[19186.071371] VFS: busy inodes on changed media.
[19188.069062] VFS: busy inodes on changed media.
[19188.070973] VFS: busy inodes on changed media.
[19190.068655] VFS: busy inodes on changed media.
[19190.070543] VFS: busy inodes on changed media.
[19192.068247] VFS: busy inodes on changed media.
[19192.071146] VFS: busy inodes on changed media.
[19194.067869] VFS: busy inodes on changed media.
[19194.069757] VFS: busy inodes on changed media.
[19196.067583] VFS: busy inodes on changed media.
[19196.069499] VFS: busy inodes on changed media.
[19198.067056] VFS: busy inodes on changed media.
[19198.068945] VFS: busy inodes on changed media.
[19200.066651] VFS: busy inodes on changed media.
[19200.068716] VFS: busy inodes on changed media.
[19202.066254] VFS: busy inodes on changed media.
[19202.068181] VFS: busy inodes on changed media.
[19204.065844] VFS: busy inodes on changed media.
[19204.067746] VFS: busy inodes on changed media.
[19206.065489] VFS: busy inodes on changed media.
[19206.067372] VFS: busy inodes on changed media.
[19208.065540] VFS: busy inodes on changed media.
[19208.067468] VFS: busy inodes on changed media.
[19210.064678] VFS: busy inodes on changed media.
[19210.066593] VFS: busy inodes on changed media.
[19212.064314] VFS: busy inodes on changed media.
[19212.066184] VFS: busy inodes on changed media.
[19214.063926] VFS: busy inodes on changed media.
[19214.065628] VFS: busy inodes on changed media.
[19216.063565] VFS: busy inodes on changed media.
[19216.065266] VFS: busy inodes on changed media.
[19218.068995] VFS: busy inodes on changed media.
[19218.071226] VFS: busy inodes on changed media.
[19220.062794] VFS: busy inodes on changed media.
[19220.064824] VFS: busy inodes on changed media.
[19222.062474] VFS: busy inodes on changed media.
[19222.064415] VFS: busy inodes on changed media.
[19224.061892] VFS: busy inodes on changed media.
[19224.063796] VFS: busy inodes on changed media.
[19226.061574] VFS: busy inodes on changed media.
[19226.063479] VFS: busy inodes on changed media.
[19228.061096] VFS: busy inodes on changed media.
[19228.063018] VFS: busy inodes on changed media.
[19230.060625] VFS: busy inodes on changed media.
[19230.062509] VFS: busy inodes on changed media.
[19232.060229] VFS: busy inodes on changed media.
[19232.062127] VFS: busy inodes on changed media.
[19234.059840] VFS: busy inodes on changed media.
[19234.061864] VFS: busy inodes on changed media.
[19236.059434] VFS: busy inodes on changed media.
[19236.062590] VFS: busy inodes on changed media.
[19238.059186] VFS: busy inodes on changed media.
[19238.061010] VFS: busy inodes on changed media.
[19240.059007] VFS: busy inodes on changed media.
[19240.060928] VFS: busy inodes on changed media.
[19242.058339] VFS: busy inodes on changed media.
[19242.070515] VFS: busy inodes on changed media.
[19244.058020] VFS: busy inodes on changed media.
[19244.060013] VFS: busy inodes on changed media.
[19246.058436] VFS: busy inodes on changed media.
[19246.060366] VFS: busy inodes on changed media.
[19248.057256] VFS: busy inodes on changed media.
[19248.059666] VFS: busy inodes on changed media.
[19250.057704] VFS: busy inodes on changed media.
[19250.060315] VFS: busy inodes on changed media.
[19252.056416] VFS: busy inodes on changed media.
[19252.058493] VFS: busy inodes on changed media.
[19254.056798] VFS: busy inodes on changed media.
[19254.058961] VFS: busy inodes on changed media.
[19256.055900] VFS: busy inodes on changed media.
[19256.057934] VFS: busy inodes on changed media.
[19258.055256] VFS: busy inodes on changed media.
[19258.057197] VFS: busy inodes on changed media.
[19260.054793] VFS: busy inodes on changed media.
[19260.056416] VFS: busy inodes on changed media.
[19262.054682] VFS: busy inodes on changed media.
[19262.057023] VFS: busy inodes on changed media.
[19264.054619] VFS: busy inodes on changed media.
[19264.057163] VFS: busy inodes on changed media.
[19266.059115] VFS: busy inodes on changed media.
[19266.062617] VFS: busy inodes on changed media.
[19268.054351] VFS: busy inodes on changed media.
[19268.057290] VFS: busy inodes on changed media.
[19270.053154] VFS: busy inodes on changed media.
[19270.055804] VFS: busy inodes on changed media.
[19272.052882] VFS: busy inodes on changed media.
[19272.055658] VFS: busy inodes on changed media.
[19274.052544] VFS: busy inodes on changed media.
[19274.055483] VFS: busy inodes on changed media.
[19276.052091] VFS: busy inodes on changed media.
[19276.054922] VFS: busy inodes on changed media.
[19278.056199] VFS: busy inodes on changed media.
[19278.059068] VFS: busy inodes on changed media.
[19280.051571] VFS: busy inodes on changed media.
[19280.054683] VFS: busy inodes on changed media.
[19282.050930] VFS: busy inodes on changed media.
[19282.053299] VFS: busy inodes on changed media.
[19284.050179] VFS: busy inodes on changed media.
[19284.052512] VFS: busy inodes on changed media.
[19286.049823] VFS: busy inodes on changed media.
[19286.052200] VFS: busy inodes on changed media.
[19288.052944] VFS: busy inodes on changed media.
[19288.054940] VFS: busy inodes on changed media.
[19290.048947] VFS: busy inodes on changed media.
[19290.051035] VFS: busy inodes on changed media.
[19292.048369] VFS: busy inodes on changed media.
[19292.050003] VFS: busy inodes on changed media.
[19294.048235] VFS: busy inodes on changed media.
[19294.049873] VFS: busy inodes on changed media.
[19296.047741] VFS: busy inodes on changed media.
[19296.049840] VFS: busy inodes on changed media.
[19298.047167] VFS: busy inodes on changed media.
[19298.048790] VFS: busy inodes on changed media.
[19300.046795] VFS: busy inodes on changed media.
[19300.048597] VFS: busy inodes on changed media.
[19302.047092] VFS: busy inodes on changed media.
[19302.048705] VFS: busy inodes on changed media.
[19304.046093] VFS: busy inodes on changed media.
[19304.048335] VFS: busy inodes on changed media.
[19306.046305] VFS: busy inodes on changed media.
[19306.049206] VFS: busy inodes on changed media.
[19308.046080] VFS: busy inodes on changed media.
[19308.049129] VFS: busy inodes on changed media.
[19310.045555] VFS: busy inodes on changed media.
[19310.048682] VFS: busy inodes on changed media.
[19312.044864] VFS: busy inodes on changed media.
[19312.047541] VFS: busy inodes on changed media.
[19314.044358] VFS: busy inodes on changed media.
[19314.047295] VFS: busy inodes on changed media.
[19316.044268] VFS: busy inodes on changed media.
[19316.046361] VFS: busy inodes on changed media.
[19318.043556] VFS: busy inodes on changed media.
[19318.045974] VFS: busy inodes on changed media.
[19320.043106] VFS: busy inodes on changed media.
[19320.045552] VFS: busy inodes on changed media.
[19322.042658] VFS: busy inodes on changed media.
[19322.045137] VFS: busy inodes on changed media.
[19324.042349] VFS: busy inodes on changed media.
[19324.045728] VFS: busy inodes on changed media.
[19326.042619] VFS: busy inodes on changed media.
[19326.045257] VFS: busy inodes on changed media.
[19328.041590] VFS: busy inodes on changed media.
[19328.044765] VFS: busy inodes on changed media.
[19330.041164] VFS: busy inodes on changed media.
[19330.043758] VFS: busy inodes on changed media.
[19332.040667] VFS: busy inodes on changed media.
[19332.043192] VFS: busy inodes on changed media.
[19334.040266] VFS: busy inodes on changed media.
[19334.042695] VFS: busy inodes on changed media.
[19336.039957] VFS: busy inodes on changed media.
[19336.042368] VFS: busy inodes on changed media.
[19338.041188] VFS: busy inodes on changed media.
[19338.043998] VFS: busy inodes on changed media.
[19340.039237] VFS: busy inodes on changed media.
[19340.041818] VFS: busy inodes on changed media.
[19342.039369] VFS: busy inodes on changed media.
[19342.042480] VFS: busy inodes on changed media.
[19344.041518] VFS: busy inodes on changed media.
[19344.044474] VFS: busy inodes on changed media.
[19346.038411] VFS: busy inodes on changed media.
[19346.041330] VFS: busy inodes on changed media.
[19348.037898] VFS: busy inodes on changed media.
[19348.040651] VFS: busy inodes on changed media.
[19350.037458] VFS: busy inodes on changed media.
[19350.041020] VFS: busy inodes on changed media.
[19352.037335] VFS: busy inodes on changed media.
[19352.039857] VFS: busy inodes on changed media.
[19354.036809] VFS: busy inodes on changed media.
[19354.039705] VFS: busy inodes on changed media.
[19356.036452] VFS: busy inodes on changed media.
[19356.039037] VFS: busy inodes on changed media.
[19358.035779] VFS: busy inodes on changed media.
[19358.038669] VFS: busy inodes on changed media.
[19360.035516] VFS: busy inodes on changed media.
[19360.038530] VFS: busy inodes on changed media.
[19362.035356] VFS: busy inodes on changed media.
[19362.037922] VFS: busy inodes on changed media.
[19364.034805] VFS: busy inodes on changed media.
[19364.037818] VFS: busy inodes on changed media.
[19366.034193] VFS: busy inodes on changed media.
[19366.036912] VFS: busy inodes on changed media.
[19368.035106] VFS: busy inodes on changed media.
[19368.037988] VFS: busy inodes on changed media.
[19370.033791] VFS: busy inodes on changed media.
[19370.036992] VFS: busy inodes on changed media.
[19372.033698] VFS: busy inodes on changed media.
[19372.036693] VFS: busy inodes on changed media.
[19374.032891] VFS: busy inodes on changed media.
[19374.036768] VFS: busy inodes on changed media.
[19376.032899] VFS: busy inodes on changed media.
[19376.035840] VFS: busy inodes on changed media.
[19378.032226] VFS: busy inodes on changed media.
[19378.034974] VFS: busy inodes on changed media.
[19380.031666] VFS: busy inodes on changed media.
[19380.034782] VFS: busy inodes on changed media.
[19382.031703] VFS: busy inodes on changed media.
[19382.034591] VFS: busy inodes on changed media.
[19384.031095] VFS: busy inodes on changed media.
[19384.033754] VFS: busy inodes on changed media.
[19386.031199] VFS: busy inodes on changed media.
[19386.034398] VFS: busy inodes on changed media.
[19388.029969] VFS: busy inodes on changed media.
[19388.032994] VFS: busy inodes on changed media.
[19390.029767] VFS: busy inodes on changed media.
[19390.032973] VFS: busy inodes on changed media.
[19392.029162] VFS: busy inodes on changed media.
[19392.032098] VFS: busy inodes on changed media.
[19394.032432] VFS: busy inodes on changed media.
[19394.036584] VFS: busy inodes on changed media.
[19396.028376] VFS: busy inodes on changed media.
[19396.031467] VFS: busy inodes on changed media.
[19398.032125] VFS: busy inodes on changed media.
[19398.035192] VFS: busy inodes on changed media.
[19400.027617] VFS: busy inodes on changed media.
[19400.030584] VFS: busy inodes on changed media.
[19402.027365] VFS: busy inodes on changed media.
[19402.030129] VFS: busy inodes on changed media.
[19404.026906] VFS: busy inodes on changed media.
[19404.030136] VFS: busy inodes on changed media.
[19406.026473] VFS: busy inodes on changed media.
[19406.029451] VFS: busy inodes on changed media.
[19408.026504] VFS: busy inodes on changed media.
[19408.029378] VFS: busy inodes on changed media.
[19410.025815] VFS: busy inodes on changed media.
[19410.028810] VFS: busy inodes on changed media.
[19412.025212] VFS: busy inodes on changed media.
[19412.028387] VFS: busy inodes on changed media.
[19414.025147] VFS: busy inodes on changed media.
[19414.028186] VFS: busy inodes on changed media.
[19416.024411] VFS: busy inodes on changed media.
[19416.027898] VFS: busy inodes on changed media.
[19418.023964] VFS: busy inodes on changed media.
[19418.026949] VFS: busy inodes on changed media.
[19420.025542] VFS: busy inodes on changed media.
[19420.028316] VFS: busy inodes on changed media.
[19422.026393] VFS: busy inodes on changed media.
[19422.029094] VFS: busy inodes on changed media.
[19424.022774] VFS: busy inodes on changed media.
[19424.025748] VFS: busy inodes on changed media.
[19426.022313] VFS: busy inodes on changed media.
[19426.025389] VFS: busy inodes on changed media.
[19428.022061] VFS: busy inodes on changed media.
[19428.025006] VFS: busy inodes on changed media.
[19430.021862] VFS: busy inodes on changed media.
[19430.024591] VFS: busy inodes on changed media.
[19432.022043] VFS: busy inodes on changed media.
[19432.025070] VFS: busy inodes on changed media.
[19434.020748] VFS: busy inodes on changed media.
[19434.023802] VFS: busy inodes on changed media.
[19436.020395] VFS: busy inodes on changed media.
[19436.023295] VFS: busy inodes on changed media.
[19438.019897] VFS: busy inodes on changed media.
[19438.023263] VFS: busy inodes on changed media.
[19440.019600] VFS: busy inodes on changed media.
[19440.022548] VFS: busy inodes on changed media.
[19442.019171] VFS: busy inodes on changed media.
[19442.022213] VFS: busy inodes on changed media.
[19444.018700] VFS: busy inodes on changed media.
[19444.020486] VFS: busy inodes on changed media.
[19446.018561] VFS: busy inodes on changed media.
[19446.021800] VFS: busy inodes on changed media.
[19448.017966] VFS: busy inodes on changed media.
[19448.020910] VFS: busy inodes on changed media.
[19450.017604] VFS: busy inodes on changed media.
[19450.020635] VFS: busy inodes on changed media.
[19452.017175] VFS: busy inodes on changed media.
[19452.020074] VFS: busy inodes on changed media.
[19454.020375] VFS: busy inodes on changed media.
[19454.023104] VFS: busy inodes on changed media.
[19456.016337] VFS: busy inodes on changed media.
[19456.019328] VFS: busy inodes on changed media.
[19458.021521] VFS: busy inodes on changed media.
[19458.025848] VFS: busy inodes on changed media.
[19460.015464] VFS: busy inodes on changed media.
[19460.018499] VFS: busy inodes on changed media.
[19462.015014] VFS: busy inodes on changed media.
[19462.017948] VFS: busy inodes on changed media.
[19464.015085] VFS: busy inodes on changed media.
[19464.018136] VFS: busy inodes on changed media.
[19466.014339] VFS: busy inodes on changed media.
[19466.017282] VFS: busy inodes on changed media.
[19468.013925] VFS: busy inodes on changed media.
[19468.016980] VFS: busy inodes on changed media.
[19470.013750] VFS: busy inodes on changed media.
[19470.016482] VFS: busy inodes on changed media.
[19472.013111] VFS: busy inodes on changed media.
[19472.016141] VFS: busy inodes on changed media.
[19474.013001] VFS: busy inodes on changed media.
[19474.015841] VFS: busy inodes on changed media.
[19476.013318] VFS: busy inodes on changed media.
[19476.018285] VFS: busy inodes on changed media.
[19478.013527] VFS: busy inodes on changed media.
[19478.016583] VFS: busy inodes on changed media.
[19480.011716] VFS: busy inodes on changed media.
[19480.014935] VFS: busy inodes on changed media.
[19482.011386] VFS: busy inodes on changed media.
[19482.014119] VFS: busy inodes on changed media.
[19484.010686] VFS: busy inodes on changed media.
[19484.013726] VFS: busy inodes on changed media.
[19486.010613] VFS: busy inodes on changed media.
[19486.013470] VFS: busy inodes on changed media.
[19488.010397] VFS: busy inodes on changed media.
[19488.013727] VFS: busy inodes on changed media.
[19490.009585] VFS: busy inodes on changed media.
[19490.012587] VFS: busy inodes on changed media.
[19492.009144] VFS: busy inodes on changed media.
[19492.012274] VFS: busy inodes on changed media.
[19494.008975] VFS: busy inodes on changed media.
[19494.011835] VFS: busy inodes on changed media.
[19496.008215] VFS: busy inodes on changed media.
[19496.011126] VFS: busy inodes on changed media.
[19498.012534] VFS: busy inodes on changed media.
[19498.015361] VFS: busy inodes on changed media.
[19500.008215] VFS: busy inodes on changed media.
[19500.012631] VFS: busy inodes on changed media.
[19502.007893] VFS: busy inodes on changed media.
[19502.010867] VFS: busy inodes on changed media.
[19504.006529] VFS: busy inodes on changed media.
[19504.009449] VFS: busy inodes on changed media.
[19506.006104] VFS: busy inodes on changed media.
[19506.009222] VFS: busy inodes on changed media.
[19508.006765] VFS: busy inodes on changed media.
[19508.009175] VFS: busy inodes on changed media.
[19510.005378] VFS: busy inodes on changed media.
[19510.008183] VFS: busy inodes on changed media.
[19512.005092] VFS: busy inodes on changed media.
[19512.007531] VFS: busy inodes on changed media.
[19514.004365] VFS: busy inodes on changed media.
[19514.007299] VFS: busy inodes on changed media.
[19516.004003] VFS: busy inodes on changed media.
[19516.007019] VFS: busy inodes on changed media.
[19518.007724] VFS: busy inodes on changed media.
[19518.011957] VFS: busy inodes on changed media.
[19520.003186] VFS: busy inodes on changed media.
[19520.006008] VFS: busy inodes on changed media.
[19522.002971] VFS: busy inodes on changed media.
[19522.005882] VFS: busy inodes on changed media.
[19524.002544] VFS: busy inodes on changed media.
[19524.005072] VFS: busy inodes on changed media.
[19526.003472] VFS: busy inodes on changed media.
[19526.006273] VFS: busy inodes on changed media.
[19528.001365] VFS: busy inodes on changed media.
[19528.003914] VFS: busy inodes on changed media.
[19530.003202] VFS: busy inodes on changed media.
[19530.005719] VFS: busy inodes on changed media.
[19532.000856] VFS: busy inodes on changed media.
[19532.003300] VFS: busy inodes on changed media.
[19534.000232] VFS: busy inodes on changed media.
[19534.002665] VFS: busy inodes on changed media.
[19536.000858] VFS: busy inodes on changed media.
[19536.003926] VFS: busy inodes on changed media.
[19537.999500] VFS: busy inodes on changed media.
[19538.004331] VFS: busy inodes on changed media.
[19539.999047] VFS: busy inodes on changed media.
[19540.001470] VFS: busy inodes on changed media.
[19541.998639] VFS: busy inodes on changed media.
[19542.001091] VFS: busy inodes on changed media.
[19543.998007] VFS: busy inodes on changed media.
[19544.000294] VFS: busy inodes on changed media.
[19546.001645] VFS: busy inodes on changed media.
[19546.004012] VFS: busy inodes on changed media.
[19547.997227] VFS: busy inodes on changed media.
[19547.999537] VFS: busy inodes on changed media.
[19549.996877] VFS: busy inodes on changed media.
[19549.999360] VFS: busy inodes on changed media.
[19551.996348] VFS: busy inodes on changed media.
[19551.998638] VFS: busy inodes on changed media.
[19553.996620] VFS: busy inodes on changed media.
[19553.999185] VFS: busy inodes on changed media.
[19555.995837] VFS: busy inodes on changed media.
[19555.997782] VFS: busy inodes on changed media.
[19557.995236] VFS: busy inodes on changed media.
[19557.997594] VFS: busy inodes on changed media.
[19559.994889] VFS: busy inodes on changed media.
[19559.997316] VFS: busy inodes on changed media.
[19561.994356] VFS: busy inodes on changed media.
[19561.996740] VFS: busy inodes on changed media.
[19563.993985] VFS: busy inodes on changed media.
[19563.996431] VFS: busy inodes on changed media.
[19565.993488] VFS: busy inodes on changed media.
[19565.995623] VFS: busy inodes on changed media.
[19567.993003] VFS: busy inodes on changed media.
[19567.995140] VFS: busy inodes on changed media.
[19569.992764] VFS: busy inodes on changed media.
[19569.996057] VFS: busy inodes on changed media.
[19571.992274] VFS: busy inodes on changed media.
[19571.994425] VFS: busy inodes on changed media.
[19573.991818] VFS: busy inodes on changed media.
[19573.994007] VFS: busy inodes on changed media.
[19575.992561] VFS: busy inodes on changed media.
[19575.994745] VFS: busy inodes on changed media.
[19577.995436] VFS: busy inodes on changed media.
[19577.997477] VFS: busy inodes on changed media.
[19579.992196] VFS: busy inodes on changed media.
[19579.994958] VFS: busy inodes on changed media.
[19581.990741] VFS: busy inodes on changed media.
[19581.992890] VFS: busy inodes on changed media.
[19583.989706] VFS: busy inodes on changed media.
[19583.991780] VFS: busy inodes on changed media.
[19585.989367] VFS: busy inodes on changed media.
[19585.991472] VFS: busy inodes on changed media.
[19587.989515] VFS: busy inodes on changed media.
[19587.992233] VFS: busy inodes on changed media.
[19589.989749] VFS: busy inodes on changed media.
[19589.992746] VFS: busy inodes on changed media.
[19591.989603] VFS: busy inodes on changed media.
[19591.992530] VFS: busy inodes on changed media.
[19593.988965] VFS: busy inodes on changed media.
[19593.992190] VFS: busy inodes on changed media.
[19595.988700] VFS: busy inodes on changed media.
[19595.991186] VFS: busy inodes on changed media.
[19597.988199] VFS: busy inodes on changed media.
[19597.991676] VFS: busy inodes on changed media.
[19599.987994] VFS: busy inodes on changed media.
[19599.991421] VFS: busy inodes on changed media.
[19601.987345] VFS: busy inodes on changed media.
[19601.990985] VFS: busy inodes on changed media.
[19603.986732] VFS: busy inodes on changed media.
[19603.990051] VFS: busy inodes on changed media.
[19605.986951] VFS: busy inodes on changed media.
[19605.990096] VFS: busy inodes on changed media.
[19607.986284] VFS: busy inodes on changed media.
[19607.989679] VFS: busy inodes on changed media.
[19609.986493] VFS: busy inodes on changed media.
[19610.022646] VFS: busy inodes on changed media.
[19611.985545] VFS: busy inodes on changed media.
[19611.989247] VFS: busy inodes on changed media.
[19613.985151] VFS: busy inodes on changed media.
[19613.988664] VFS: busy inodes on changed media.
[19615.984663] VFS: busy inodes on changed media.
[19615.988005] VFS: busy inodes on changed media.
[19617.984354] VFS: busy inodes on changed media.
[19617.987442] VFS: busy inodes on changed media.
[19619.983767] VFS: busy inodes on changed media.
[19619.987118] VFS: busy inodes on changed media.
[19621.983796] VFS: busy inodes on changed media.
[19621.987275] VFS: busy inodes on changed media.
[19623.982768] VFS: busy inodes on changed media.
[19623.985918] VFS: busy inodes on changed media.
[19625.982416] VFS: busy inodes on changed media.
[19625.986018] VFS: busy inodes on changed media.
[19627.985633] VFS: busy inodes on changed media.
[19627.988958] VFS: busy inodes on changed media.
[19629.981779] VFS: busy inodes on changed media.
[19629.984459] VFS: busy inodes on changed media.
[19631.980779] VFS: busy inodes on changed media.
[19631.983596] VFS: busy inodes on changed media.
[19633.980584] VFS: busy inodes on changed media.
[19633.984098] VFS: busy inodes on changed media.
```

---

### Post by cova on 2008-06-30
EDIT: Sorry, double post!

---

### Post by xc3RnbFO8P on 2008-06-30
> sudo gedit /etc/modprobe.d/option
add this line: **options dvb_usb_dib0700 force_lna_activation=1**
save and restart the computer.
Run **dmesg** again.

---

### Post by xc3RnbFO8P on 2008-06-30
Thread from SuperMike [http://ubuntuforums.org/showthread.php?t=529096]("http://ubuntuforums.org/showthread.php?t=529096")
> VFS: busy inodes on changed media.

 WORKAROUND -- VFS: busy inodes on changed media.
Do you have Fiesty and find that, after ejecting a CDROM manually by the button that your /var/log/messages (System Log) starts to flood with the following error?

VFS: busy inodes on changed media.

The workaround appears to be the following two steps, even if you have no CDROM in the drive at this point:

1. Open Terminal
2. sudo eject
3. Let it eject and then push the button on your drive to pull the empty CD tray back in.
4. sudo eject -t
5. exit

By doing this, I found that it stopped flooding the System Log.

---

### Post by cova on 2008-06-30
Ok here we go
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-17-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu May 1 14:31:33 UTC 2008 (Ubuntu 2.6.24-17.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000bff0000 (usable)
[    0.000000]  BIOS-e820: 000000000bff0000 - 000000000bff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000bff3000 - 000000000c000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 191MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 49136) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    49136
[    0.000000]   HighMem     49136 ->    49136
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    49136
[    0.000000] On node 0 totalpages: 49136
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 351 pages used for memmap
[    0.000000]   Normal zone: 44689 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7620 checksum 0
[    0.000000] ACPI: RSDP 000F7620, 0014 (r0 JETWAY)
[    0.000000] ACPI: RSDT 0BFF3000, 0028 (r1 JETWAY AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 0BFF3040, 0074 (r1 JETWAY AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 0BFF30C0, 3817 (r1 JETWAY AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 0BFF0000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x5008
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f3ff0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 48753
[    0.000000] Kernel command line: root=UUID=f96ad0bf-e962-4d23-99bd-3a8097ee8c6a ro lapic pci=routeirq
[    0.000000] Local APIC disabled by BIOS -- reenabling.
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 803.652 MHz processor.
[   39.548710] Console: colour VGA+ 80x25
[   39.548721] console [tty0] enabled
[   39.551393] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   39.552103] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   39.572284] Memory: 182916k/196544k available (2176k kernel code, 13132k reserved, 1007k data, 368k init, 0k highmem)
[   39.572389] virtual kernel memory layout:
[   39.572392]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   39.572396]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   39.572399]     vmalloc : 0xcc800000 - 0xff7fe000   ( 815 MB)
[   39.572403]     lowmem  : 0xc0000000 - 0xcbff0000   ( 191 MB)
[   39.572406]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   39.572409]       .data : 0xc0320134 - 0xc041bdc4   (1007 kB)
[   39.572413]       .text : 0xc0100000 - 0xc0320134   (2176 kB)
[   39.572842] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   39.573072] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   39.653168] Calibrating delay using timer specific routine.. 1608.60 BogoMIPS (lpj=3217218)
[   39.653362] Security Framework initialized
[   39.653434] SELinux:  Disabled at boot.
[   39.653551] AppArmor: AppArmor initialized
[   39.653618] Failure registering capabilities with primary security module.
[   39.653703] Mount-cache hash table entries: 512
[   39.654170] Initializing cgroup subsys ns
[   39.654241] Initializing cgroup subsys cpuacct
[   39.654326] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   39.654351] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   39.654415] CPU: L2 Cache: 64K (64 bytes/line)
[   39.654474] CPU: After all inits, caps: 0183fbff c1c7fbff 00000000 00000420 00000000 00000000 00000000 00000000
[   39.654512] Compat vDSO mapped to ffffe000.
[   39.654606] Checking 'hlt' instruction... OK.
[   39.669340] SMP alternatives: switching to UP code
[   39.672628] Freeing SMP alternatives: 11k freed
[   39.673099] Early unpacking initramfs... done
[   40.564503] ACPI: Core revision 20070126
[   40.564849] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   40.568425] ACPI: setting ELCR to 0200 (from 0c20)
[   40.572358] CPU0: AMD Duron(tm) processor stepping 01
[   40.572484] SMP motherboard not detected.
[   40.677209] Brought up 1 CPUs
[   40.677337] CPU0 attaching sched-domain:
[   40.677345]  domain 0: span 01
[   40.677349]   groups: 01
[   40.678100] net_namespace: 64 bytes
[   40.678188] Booting paravirtualized kernel on bare hardware
[   40.679507] Time: 22:43:34  Date: 06/30/08
[   40.679687] NET: Registered protocol family 16
[   40.680474] EISA bus registered
[   40.680593] ACPI: bus type pci registered
[   40.753418] PCI: PCI BIOS revision 2.10 entry at 0xfb2d0, last bus=1
[   40.753505] PCI: Using configuration type 1
[   40.753561] Setting up standard PCI resources
[   40.764071] ACPI: EC: Look up EC in DSDT
[   40.770738] ACPI: Interpreter enabled
[   40.770825] ACPI: (supports S0 S1 S4 S5)
[   40.771025] ACPI: Using PIC for interrupt routing
[   40.784504] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   40.785686] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   40.813300] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   40.814122] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   40.814832] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   40.815537] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   40.816499] Linux Plug and Play Support v0.97 (c) Adam Belay
[   40.816703] pnp: PnP ACPI init
[   40.816793] ACPI: bus type pnp registered
[   40.826994] pnp: PnP ACPI: found 14 devices
[   40.827079] ACPI: ACPI bus type pnp unregistered
[   40.827143] PnPBIOS: Disabled by ACPI PNP
[   40.828076] PCI: Using ACPI for IRQ routing
[   40.828153] PCI: Routing PCI interrupts for all devices because "pci=routeirq" specified
[   40.829196] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   40.829268] PCI: setting IRQ 10 as level-triggered
[   40.829276] ACPI: PCI Interrupt 0000:00:01.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   40.829423] ACPI: PCI Interrupt 0000:00:01.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   40.830057] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   40.830119] PCI: setting IRQ 5 as level-triggered
[   40.830125] ACPI: PCI Interrupt 0000:00:01.4[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   40.830267] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   40.831014] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   40.831076] PCI: setting IRQ 11 as level-triggered
[   40.831082] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   40.834892] spurious 8259A interrupt: IRQ7.
[   40.881061] NET: Registered protocol family 8
[   40.881136] NET: Registered protocol family 20
[   40.881563] AppArmor: AppArmor Filesystem Enabled
[   40.885028] Time: tsc clocksource has been installed.
[   40.893251] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[   40.893322] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[   40.893386] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   40.893449] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   40.893514] system 00:00: iomem range 0xbff0000-0xbffffff could not be reserved
[   40.893593] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   40.893670] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   40.893732] system 00:00: iomem range 0x100000-0xbfeffff could not be reserved
[   40.893809] system 00:00: iomem range 0xffee0000-0xffefffff has been reserved
[   40.893873] system 00:00: iomem range 0xfffe0000-0xfffeffff has been reserved
[   40.893937] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[   40.894021] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   40.894084] system 00:02: ioport range 0x294-0x297 has been reserved
[   40.925583] PCI: Bridge: 0000:00:02.0
[   40.925660]   IO window: c000-cfff
[   40.925719]   MEM window: dc000000-dc0fffff
[   40.925777]   PREFETCH window: d0000000-d7ffffff
[   40.925853] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   40.925906] NET: Registered protocol family 2
[   40.965328] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   40.966044] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   40.966560] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   40.967077] TCP: Hash tables configured (established 8192 bind 8192)
[   40.967141] TCP reno registered
[   40.977531] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   41.707349]  it is
[   42.643120] Freeing initrd memory: 7254k freed
[   42.645304] audit: initializing netlink socket (disabled)
[   42.645428] audit(1214865814.968:1): initialized
[   42.652025] VFS: Disk quotas dquot_6.5.1
[   42.652414] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   42.653158] io scheduler noop registered
[   42.653233] io scheduler anticipatory registered
[   42.653290] io scheduler deadline registered
[   42.653389] io scheduler cfq registered (default)
[   42.653538] Boot video device is 0000:01:00.0
[   42.654508] isapnp: Scanning for PnP cards...
[   43.008346] isapnp: No Plug & Play device found
[   43.215626] Real Time Clock Driver v1.12ac
[   43.216024] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   43.216423] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   43.217361] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   43.220016] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   43.221646] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   43.224811] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   43.225202] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   43.225639] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   43.226217] serio: i8042 KBD port at 0x60,0x64 irq 1
[   43.226290] serio: i8042 AUX port at 0x60,0x64 irq 12
[   43.233090] mice: PS/2 mouse device common for all mice
[   43.233659] EISA: Probing bus 0 at eisa.0
[   43.233756] Cannot allocate resource for EISA slot 4
[   43.233814] Cannot allocate resource for EISA slot 5
[   43.233887] EISA: Detected 0 cards.
[   43.233947] cpuidle: using governor ladder
[   43.234001] cpuidle: using governor menu
[   43.234622] NET: Registered protocol family 1
[   43.234786] Using IPI No-Shortcut mode
[   43.234980] registered taskstats version 1
[   43.235292]   Magic number: 12:274:756
[   43.235916] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   43.236613] EDD information not available.
[   43.238440] Freeing unused kernel memory: 368k freed
[   43.254690] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   44.081373] fuse init (API version 7.9)
[   44.140976] ACPI: Fan [FAN] (on)
[   44.293142] ACPI: Thermal Zone [THRM] (38 C)
[   45.362099] SCSI subsystem initialized
[   45.644124] libata version 3.00 loaded.
[   45.718034] usbcore: registered new interface driver usbfs
[   45.718190] usbcore: registered new interface driver hub
[   45.749273] pata_sis 0000:00:00.1: version 0.5.2
[   45.781161] usbcore: registered new device driver usb
[   45.807877] scsi0 : pata_sis
[   45.848274] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   45.868123] scsi1 : pata_sis
[   45.869560] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x4000 irq 14
[   45.869636] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x4008 irq 15
[   46.032611] ata1.00: native sectors (39102335) is smaller than sectors (39102336)
[   46.032726] ata1.00: ATA-5: ST320413A, 3.40, max UDMA/100
[   46.032787] ata1.00: 39102336 sectors, multi 16: LBA 
[   46.048493] ata1.00: configured for UDMA/100
[   46.368180] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   46.748250] Floppy drive(s): fd0 is 1.44M
[   46.767806] FDC 0 is a post-1991 82077
[   51.086976] ata2: port is slow to respond, please be patient (Status 0x80)
[   56.069964] ata2: device not ready (errno=-16), forcing hardreset
[   56.237663] scsi 0:0:0:0: Direct-Access     ATA      ST320413A        3.40 PQ: 0 ANSI: 5
[   56.242639] ACPI: PCI Interrupt 0000:00:01.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   56.242850] ohci_hcd 0000:00:01.2: OHCI Host Controller
[   56.244232] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[   56.244363] ohci_hcd 0000:00:01.2: irq 10, io mem 0xdc110000
[   56.300489] usb usb1: configuration #1 chosen from 1 choice
[   56.300653] hub 1-0:1.0: USB hub found
[   56.300729] hub 1-0:1.0: 3 ports detected
[   56.402344] ACPI: PCI Interrupt 0000:00:01.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   56.402549] ohci_hcd 0000:00:01.3: OHCI Host Controller
[   56.402684] ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
[   56.402797] ohci_hcd 0000:00:01.3: irq 10, io mem 0xdc111000
[   56.460288] usb usb2: configuration #1 chosen from 1 choice
[   56.460446] hub 2-0:1.0: USB hub found
[   56.460522] hub 2-0:1.0: 3 ports detected
[   56.563646] 8139cp 0000:00:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   56.563754] 8139cp 0000:00:09.0: Try the "8139too" driver instead.
[   56.573512] 8139too Fast Ethernet driver 0.9.28
[   56.573788] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   56.575009] eth0: RealTek RTL8139 at 0xdc00, 00:17:3f:ce:34:6c, IRQ 5
[   56.575075] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   56.625599] Driver 'sd' needs updating - please use bus_type methods
[   56.626063] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[   56.626171] sd 0:0:0:0: [sda] Write Protect is off
[   56.626231] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   56.626290] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   56.626537] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[   56.626625] sd 0:0:0:0: [sda] Write Protect is off
[   56.626683] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   56.627123] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   56.627222]  sda: sda1 sda2 < sda5 >
[   56.697695] sd 0:0:0:0: [sda] Attached SCSI disk
[   56.698267] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   56.720101] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   56.918137] usb 1-1: configuration #1 chosen from 1 choice
[   57.791224] Attempting manual resume
[   57.791292] swsusp: Resume From Partition 8:5
[   57.791297] PM: Checking swsusp image.
[   57.798212] PM: Resume from disk failed.
[   57.914168] kjournald starting.  Commit interval 5 seconds
[   57.914293] EXT3-fs: mounted filesystem with ordered data mode.
[   77.513834] Linux agpgart interface v0.102
[   77.600438] agpgart: Detected SiS chipset - id:1840
[   77.683859] agpgart: AGP aperture is 64M @ 0xd8000000
[   78.373820] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   78.473207] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   79.128574] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   79.773899] input: Power Button (FF) as /devices/virtual/input/input3
[   79.805208] ACPI: Power Button (FF) [PWRF]
[   79.805789] input: Power Button (CM) as /devices/virtual/input/input4
[   79.817649] ACPI: Power Button (CM) [PWRB]
[   79.818186] input: Sleep Button (CM) as /devices/virtual/input/input5
[   79.837222] ACPI: Sleep Button (CM) [FUTS]
[   81.892863] logips2pp: Detected unknown logitech mouse model 89
[   82.366132] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   82.608789] dib0700: loaded with support for 7 different device-types
[   82.611968] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[   84.884715] ACPI: PCI Interrupt 0000:00:01.4[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   85.356690] parport_pc 00:0a: reported by Plug and Play ACPI
[   85.356836] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   86.732577] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2061: AC'97 1 does not respond - RESET
[   86.791546] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2070: AC'97 1 access is not valid [0x0], removing mixer.
[   86.799215] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3005: SI7018: the secondary codec - invalid access
[   86.816729] gameport: Trident 4DWave is pci0000:00:01.4/gameport0, speed 2130kHz
[   90.840473] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   95.748553] dib0700: firmware started successfully.
[   96.249943] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   96.250225] dvb-usb: This USB2.0 device cannot be run on a USB1.1 port. (it lacks a hardware PID filter)
[   96.250379] dvb-usb: Hauppauge Nova-T Stick error while loading driver (-19)
[   96.250516] usbcore: registered new interface driver dvb_usb_dib0700
[   96.917559] lp0: using parport0 (interrupt-driven).
[   97.132597] Adding 859436k swap on /dev/sda5.  Priority:-1 extents:1 across:859436k
[   97.794844] EXT3 FS on sda1, internal journal
[   99.925372] ip_tables: (C) 2000-2006 Netfilter Core Team
[  102.348529] No dock devices found.
[  103.318107] powernow: No powernow capabilities detected
[  105.967622] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  105.967644] apm: overridden by ACPI.
[  106.257810] ppdev: user-space parallel port driver
[  106.571783] audit(1214865879.967:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5087 profile="/usr/sbin/cupsd" namespace="default"
[  114.154412] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  114.549850] Bluetooth: Core ver 2.11
[  114.552425] NET: Registered protocol family 31
[  114.552444] Bluetooth: HCI device and connection manager initialized
[  114.552458] Bluetooth: HCI socket layer initialized
[  114.658367] Bluetooth: L2CAP ver 2.9
[  114.658388] Bluetooth: L2CAP socket layer initialized
[  114.711770] Bluetooth: RFCOMM socket layer initialized
[  114.711842] Bluetooth: RFCOMM TTY layer initialized
[  114.711848] Bluetooth: RFCOMM ver 1.8
[  117.994403] NET: Registered protocol family 17
[  123.556697] NET: Registered protocol family 10
[  123.558457] lo: Disabled Privacy Extensions
[  134.366299] eth0: no IPv6 routers present

```
Also useful to know that about the cd eject

---

### Post by xc3RnbFO8P on 2008-06-30
How old is your computer?
Do you have another usb port?

> [   90.840473] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   95.748553] dib0700: firmware started successfully.
[   96.249943] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   96.250225] dvb-usb: [COLOR="SeaGreen"]This USB2.0[/COLOR] device cannot be run on a [COLOR="Red"]USB1.1 port[/COLOR]. (it lacks a hardware PID filter)
[   96.250379] dvb-usb: Hauppauge Nova-T Stick error while loading driver (-19)
[   96.250516] usbcore: registered new interface driver dvb_usb_dib0700


---

### Post by cova on 2008-06-30
Yes its a hunk of junk i had lying around from the stone-age that was my backup until major catastrophe struck my main pc. Using a USB extension though which may be part of the problem.. Ill try without the extension
EDIT: No joy. Ah well. Looks like another thing to add to my list of things to buy with next months paycheck along with a sound card, graphics card, ram and a dvd burner!

---

### Post by xc3RnbFO8P on 2008-06-30
Good luck:)

---

