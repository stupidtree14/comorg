Q1:照簡報內容完成

Q2:
gem5/configs/common/Caches.py

gem5/configs/common/Options.py

gem5/src/cpu/BaseCPU.py

gem5/src/mem/XBar.py

gem5/configs/common/CacheConfig.py

修改這五個檔案


Q3:
./build/X86/gem5.opt configs/example/se.py \
-c ../benchmark/quicksort --cpu-type=TimingSimpleCPU \
--caches --l1i_size=32kB --l1d_size=32kB --l2cache --l2_size=128kB \
--l3cache --l3_size=1MB --l3_assoc=16384 --mem-type=NVMainMemory \
--nvmain-config=../NVmain/Config/PCM_ISSCC_2012_4GB.config > cmdlog_full-way.txt
./build/X86/gem5.opt configs/example/se.py \
-c ../benchmark/quicksort --cpu-type=TimingSimpleCPU \
--caches --l1i_size=32kB --l1d_size=32kB --l2cache --l2_size=128kB \
--l3cache --l3_size=1MB --l3_assoc=2 --mem-type=NVMainMemory \
--nvmain-config=../NVmain/Config/PCM_ISSCC_2012_4GB.config > cmdlog_2-way.txt

調整--l3_ccassoc

Q4:

加入

gem5/src/mem/cache/replacement_policies/fb_rp.cc

gem5/src/mem/cache/replacement_policies/fb_rp.hh

調整

gem5/src/mem/cache/replacement_policies/ReplacementPolicies.py

gem5/src/mem/cache/replacement_policies/SConscript

gem5/configs/common/Caches.py
