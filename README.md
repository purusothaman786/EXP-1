# Experiment 1: Decentralized Certificate Verification
### Name: PURUSOTHAMAN K
### Reg no: 212224110046
### Department: CSE(IOT)
## Aim:
To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery
and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Code:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree,
uint256 year) public {
require(msg.sender == university, "Only university can issue
certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree,
year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree,
uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree,
year));
return certificates[certHash];
}
}
```
## Expected Output:

● When the university issues a certificate, it gets stored as a hash.

● A student or employer can verify the certificate by entering the details.

● If valid, it returns true; otherwise, false.

## Output:

![WhatsApp Image 2026-02-05 at 9 19 02 AM](https://github.com/user-attachments/assets/9e0509c5-1e97-4b81-bdda-ce4e7b04543f)

## High-Level Overview:

● Used to prevent fake certificates.

● Enables quick verification by employers or other institutions.

● Shows how blockchain can be used in education and credential verification.

## Result:

Thus the smart contract for issuing and verifying academic certificates on Ethereum is successfully deployed.
