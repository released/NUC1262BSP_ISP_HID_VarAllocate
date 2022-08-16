# NUC1262BSP_ISP_HID_VarAllocate
 NUC1262BSP_ISP_HID_VarAllocate


update @ 2022/08/16

1. LDROM : use BSP \SampleCode\ISP\ISP_HID sample code , with flag in SRAM (without initial) to control update flow

2. APROM : by terminal , digit 1 , will set flag to 0x5A5A , and reboot to LDROM , to start USB ISP flow

- since use below function , to jump to LDROM , either enable boot from LDROM or boot from APROM , both acceptable in ICP config setting

				SYS_UnlockReg();
				
				FMC_SELECT_NEXT_BOOT(1);
				
				SYS_ResetCPU();

3. use ISP programming tool (USB) , to programming APROM , project 01 and project 02

![image](https://github.com/released/NUC1262BSP_ISP_HID_VarAllocate/blob/main/ISP_config.jpg)

4. below is ICP config setting , set boot as LDROM

![image](https://github.com/released/NUC1262BSP_ISP_HID_VarAllocate/blob/main/ICP_config.jpg)

5. below is KEIL config setting , to use SRAM last 16 bytes and not init to store data

![image](https://github.com/released/NUC1262BSP_ISP_HID_VarAllocate/blob/main/KEIL_config.jpg)

6. 

when under application code : PROJECT_01 , press digit 1 , to set flag in SRAM and reset to LDROM

open ISP tool , select USB and connect , then select target application code to update ARPOM

![image](https://github.com/released/NUC1262BSP_ISP_HID_VarAllocate/blob/main/log_when_under_project_01.jpg)

when under application code : PROJECT_02 , press digit 1 , to set flag in SRAM and reset to LDROM

open ISP tool , select USB and connect , then select target application code to update ARPOM

![image](https://github.com/released/NUC1262BSP_ISP_HID_VarAllocate/blob/main/log_when_under_project_02.jpg)


