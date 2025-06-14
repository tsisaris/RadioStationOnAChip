# RadioStationOnAChip
RF-Optimized PCB Design Specification
SI4735 Receiver & QN8007B Transceiver Integration
Overview
Compact, RF-optimized PCB integrating SI4735 AM/FM/SW receiver and QN8007B FM transceiver with complete RF signal path, amplification, and switching capabilities.
Component List
Primary ICs:
    • U1: SI4735-D60-GU (SSOP-24-150mil) - AM/FM/SW Receiver 
    • U2: QN8007B (QFN24 4x4mm) - FM Transceiver 
Crystals/Oscillators:
    • X1: ECS-327TXO - 32.768kHz SMD TCXO (3.28 x 2.5 x 1.3 mm) 
    • X2: ECS-TXO-2520-33-240-AN-TR - 24MHz TCXO (2.5 x 2.0 x 0.9 mm) 
RF Components:
    • U3: 2SK3557 (7-TBEX) - Low Noise Amplifier 
    • U4: LTC3121EDE#TRPBF (DFN-12) - 15V Boost Converter 
    • U5: TAV1-551+ (SOT-89) - FM Power Amplifier 
    • U6: SKY13351-378LF (DFN-6-EP) - SPDT RF Switch A (Antenna Select) 
    • U7: SKY13351-378LF (DFN-6-EP) - SPDT RF Switch B (Path Select) 
Connectors:
    • J1: FM Antenna (U.FL/IPEX) 
    • J2: AM Antenna (U.FL/IPEX) 
    • J3: GPIO Header (40-pin) 
Power Requirements
    • 5V Supply: RF components (U3-U7 via boost converter) 
    • 3.3V Supply: Digital ICs (U1, U2, oscillators) 
    • Ground: Common ground plane 
Complete Pin-to-Pin Connection Table
Component
Pin
Function
Net Name
Connected To
U1 (SI4735-D60-GU)




U1
1
DOUT
I2S_DATA_OUT
GPIO-1
U1
2
DFS
I2S_WS
U2-15, GPIO-2
U1
3
GPO3/DCLK
I2S_MCK
U2-13, GPIO-3
U1
4
GPO2/INT
SI4735_INT
GPIO-4
U1
5
GPO1
SI4735_GPO1
GPIO-5
U1
6
NC
GND
GND
U1
7
NC
GND
GND
U1
8
FMI
SI4735_FMI
U7-2 (Switch B RF1)
U1
9
RFGND
GND
GND
U1
10
NC
GND
GND
U1
11
NC
GND
GND
U1
12
AMI
SI4735_AMI
C20, GPIO-6
U1
13
GND
GND
GND
U1
14
GND
GND
GND
U1
15
RST
SI4735_RST
GPIO-7
U1
16
SEN
SI4735_SEN
GPIO-8
U1
17
SCLK
SI4735_SCLK
GPIO-9
U1
18
SDIO
SI4735_SDIO
GPIO-10
U1
19
RCLK
RCLK_32K
X1-3, R3
U1
20
VD
3V3
3V3, C1
U1
21
VA
3V3
3V3, C2
U1
22
DBYP
SI4735_DBYP
GPIO-11
U1
23
ROUT
SI4735_ROUT
GPIO-12
U1
24
LOUT
SI4735_LOUT
GPIO-13
U2 (QN8007B)




U2
1
NC
NC
No Connection
U2
2
NC
NC
No Connection
U2
3
AUGND
GND
GND
U2
4
ALI
QN8007B_ALI
GPIO-14
U2
5
ARI
QN8007B_ARI
GPIO-15
U2
6
AGND
GND
GND
U2
7
RFI
QN8007B_RFI
U7-1 (Switch B RFC)
U2
8
RFGND
GND
GND
U2
9
RFO
QN8007B_RFO
C21, U5-2
U2
10
VIO
3V3
3V3, C3
U2
11
CEN
QN8007B_CEN
GPIO-16
U2
12
MOD
QN8007B_MOD
GPIO-17
U2
13
MCK
I2S_MCK
U1-3, GPIO-3
U2
14
INT
QN8007B_INT
GPIO-18
U2
15
WS
I2S_WS
U1-2, GPIO-2
U2
16
XCLK
XCLK_24M
X2-3, R4
U2
17
XTAL1
NC
No Connection
U2
18
XTAL2
NC
No Connection
U2
19
AGND
GND
GND
U2
20
DIN
I2S_DATA_IN
GPIO-19
U2
21
SEB
QN8007B_SEB
GPIO-20
U2
22
SCL
I2C_SCL
GPIO-21, R5
U2
23
SDA
I2C_SDA
GPIO-22, R6
U2
24
VCC
3V3
3V3, C4
U2
25
PAD
GND
GND
X1 (32.768kHz TCXO)




X1
1
OE
3V3
3V3, R1
X1
2
GND
GND
GND
X1
3
OUT
RCLK_32K
U1-19, R3
X1
4
VDD
3V3
3V3, C5
X2 (24MHz TCXO)




X2
1
TRI
3V3
3V3, R2
X2
2
GND
GND
GND
X2
3
OUT
XCLK_24M
U2-16, R4
X2
4
VDD
3V3
3V3, C6
U3 (2SK3557 LNA)




U3
1
S (Source)
GND
GND
U3
2
D (Drain)
LNA_OUT
C7, U6-2, L1
U3
3
G (Gate)
LNA_IN
C8, U6-1, R7, R8
U4 (LTC3121 Boost)




U4
1
SW
BOOST_SW
L2, C9
U4
2
PGND
GND
GND
U4
3
VIN
5V
5V, C10
U4
4
PWM/SYNC
NC
No Connection
U4
5
VCC
5V
5V
U4
6
RT
BOOST_RT
R9, C11
U4
7
VC
BOOST_VC
R10, C12
U4
8
FB
BOOST_FB
R11, R12
U4
9
SD
BOOST_SD
GPIO-23
U4
10
SGND
GND
GND
U4
11
VOUT
15V
15V, C13, C14
U4
12
CAP
BOOST_CAP
C15
U4
EP
GND
GND
GND
U5 (TAV1-551+ PA)




U5
1
GND
GND
GND
U5
2
RF_IN
PA_IN
C16, U2-9
U5
3
GND
GND
GND
U5
4
RF_OUT
PA_OUT
C17, L3, C18, J1
U5
PAD
GND
GND
GND
U6 (Switch A - Antenna Select)




U6
1
RFC
ANT_COMMON
C19, U3-3
U6
2
RF1
FM_ANT
J1
U6
3
GND
GND
GND
U6
4
V1
SWITCH_A_V1
GPIO-24
U6
5
V2
SWITCH_A_V2
GPIO-25
U6
6
VDD
5V
5V, C22
U6
EP
GND
GND
GND
U7 (Switch B - Path Select)




U7
1
RFC
PATH_COMMON
U2-7, U3-2
U7
2
RF1
RX_PATH
U1-8
U7
3
GND
GND
GND
U7
4
V1
SWITCH_B_V1
GPIO-26
U7
5
V2
SWITCH_B_V2
GPIO-27
U7
6
VDD
5V
5V, C23
U7
EP
GND
GND
GND
Passive Components
Designator
Value
Function
Connection
Power Decoupling



C1
0.1µF
U1 VD bypass
U1-20 to GND
C2
0.1µF
U1 VA bypass
U1-21 to GND
C3
0.1µF
U2 VIO bypass
U2-10 to GND
C4
0.1µF
U2 VCC bypass
U2-24 to GND
C5
0.1µF
X1 VDD bypass
X1-4 to GND
C6
0.1µF
X2 VDD bypass
X2-4 to GND
LNA Biasing



R7
100kΩ
Gate bias to GND
U3-3 to GND
R8
100kΩ
Gate pullup
U3-3 to 3V3
L1
10µH
Drain RF choke
U3-2 to 3V3
RF Coupling



C7
100pF
LNA output DC block
U3-2 to U7-1
C8
100pF
LNA input DC block
U6-1 to U3-3
C16
100pF
PA input DC block
U2-9 to U5-2
C17
100pF
PA output DC block
U5-4 to antenna
C19
100pF
Antenna switch DC block
U6-1 to antenna
C20
100pF
AM antenna DC block
U1-12 to J2
C21
100pF
QN8007B RFO DC block
U2-9 coupling
Oscillator Support



R1
10kΩ
X1 output enable pullup
X1-1 to 3V3
R2
10kΩ
X2 tri-state pullup
X2-1 to 3V3
R3
33Ω
X1 output series resistor
X1-3 to U1-19
R4
33Ω
X2 output series resistor
X2-3 to U2-16
I2C Pullups



R5
4.7kΩ
SCL pullup
I2C_SCL to 3V3
R6
4.7kΩ
SDA pullup
I2C_SDA to 3V3
Boost Converter



L2
10µH
Boost inductor
U4-1 switching
C9
22µF
Boost switch cap
U4-1 filtering
C10
10µF
Input capacitor
U4-3 to GND
R9
100kΩ
Timing resistor
U4-6 to GND
C11
100pF
Timing capacitor
U4-6 to GND
R10
10kΩ
Compensation
U4-7 network
C12
1nF
Compensation
U4-7 network
R11
10kΩ
Feedback upper
U4-8 to 15V
R12
2.2kΩ
Feedback lower
U4-8 to GND
C13
22µF
Output capacitor
U4-11 to GND
C14
0.1µF
Output bypass
U4-11 to GND
C15
1µF
Bootstrap cap
U4-12 to GND
PA Matching



L3
10nH
Output matching
PA output
C18
10pF
Output matching
PA output
Switch Decoupling



C22
0.1µF
Switch A bypass
U6-6 to GND
C23
0.1µF
Switch B bypass
U7-6 to GND
GPIO Header Pinout (J3)
GPIO Pin
Net Name
Function
GPIO-1
I2S_DATA_OUT
SI4735 digital audio out
GPIO-2
I2S_WS
I2S word select (shared)
GPIO-3
I2S_MCK
I2S master clock (shared)
GPIO-4
SI4735_INT
SI4735 interrupt
GPIO-5
SI4735_GPO1
SI4735 general purpose output
GPIO-6
SI4735_AMI
AM antenna input
GPIO-7
SI4735_RST
SI4735 reset
GPIO-8
SI4735_SEN
SI4735 serial enable
GPIO-9
SI4735_SCLK
SI4735 serial clock
GPIO-10
SI4735_SDIO
SI4735 serial data I/O
GPIO-11
SI4735_DBYP
SI4735 digital bypass
GPIO-12
SI4735_ROUT
SI4735 right audio out
GPIO-13
SI4735_LOUT
SI4735 left audio out
GPIO-14
QN8007B_ALI
QN8007B left audio in
GPIO-15
QN8007B_ARI
QN8007B right audio in
GPIO-16
QN8007B_CEN
QN8007B chip enable
GPIO-17
QN8007B_MOD
QN8007B modulation
GPIO-18
QN8007B_INT
QN8007B interrupt
GPIO-19
I2S_DATA_IN
QN8007B digital audio in
GPIO-20
QN8007B_SEB
QN8007B serial enable
GPIO-21
I2C_SCL
I2C clock
GPIO-22
I2C_SDA
I2C data
GPIO-23
BOOST_SD
Boost converter shutdown
GPIO-24
SWITCH_A_V1
Antenna switch control 1
GPIO-25
SWITCH_A_V2
Antenna switch control 2
GPIO-26
SWITCH_B_V1
Path switch control 1
GPIO-27
SWITCH_B_V2
Path switch control 2
GPIO-28
3V3
3.3V supply
GPIO-29
5V
5V supply
GPIO-30
GND
Ground
RF Signal Path
    1. Reception: Antenna → Switch A → LNA → Switch B → SI4735 
    2. Transmission: QN8007B → PA → Antenna (FM) 
    3. Switch A: Selects between FM and AM antennas 
    4. Switch B: Routes signal between RX (SI4735) and TX (QN8007B) paths 
PCB Design Guidelines
    • Use 4-layer PCB with dedicated ground plane 
    • Maintain 50Ω impedance for RF traces 
    • Keep crystal traces short and shielded 
    • Use ground stitching vias around RF components 
    • Separate analog and digital ground domains where possible 
    • Add test points for all major signals 
    • Consider shield cans for LNA and PA sections 
Power Domains
    • 3.3V: Digital ICs, oscillators, logic 
    • 5V: RF switches, boost converter input 
    • 15V: Generated by boost converter (future use) 
    • GND: Common ground plane 







