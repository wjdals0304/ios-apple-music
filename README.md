# 애플뮤직 클론 코딩 
- 패스트캠퍼스 iOS 앱 개발 올인원 패키지 Online 클론코딩  

<img src="https://user-images.githubusercontent.com/26668309/146719605-d90cf871-14a5-462a-9719-31ae6a70901d.png" width = 30%> <img src="https://user-images.githubusercontent.com/26668309/146721716-fe608f3c-879c-4716-8511-2c7542a28f90.png" width = 30%> 


# 사용요소 

- UICollectionReusableView , collectionView , AVFoundation 



# 새로 배운 내용 

 -  UICollectionReusableView  
 
 ```
   func collectionView(_ collectionView: UICollectionView, viewForSupplementaryElementOfKind kind: String, at indexPath: IndexPath) -> UICollectionReusableView {
        
        switch kind {
        case UICollectionView.elementKindSectionHeader:
          .... 
          
        default :
           return UICollectionReusableView() 
           
 
 ```
 

 -  cell 클릭 이벤트 call back clouser 

``` 
 class TrackCollectionHeaderView: UICollectionReusableView {

    var tapHandler: ((AVPlayerItem) -> Void)?
   @IBAction func cardTapped(_ sender: UIButton) {
        // TODO: 탭했을때 처리
        
        guard let todaysItem = item else { return }
        tapHandler?(todaysItem)
        
    }
   }
   
   
   ------------------------------------------------------------
   
 ViewController 
   
   
  cell.tapHandler = { item -> Void in
                // player 를 띄운다
                let playerStoryboard = UIStoryboard.init(name: "Player", bundle: nil)
                guard let playerVC = playerStoryboard.instantiateViewController(withIdentifier: "PlayerViewController") as? PlayerViewController else { return }
                
                playerVC.simplePlayer.replaceCurrentItem(with: item)
                
                self.present(playerVC, animated: true, completion: nil)
                
                
                
                print("----> item title : \(item.convertToTrack()?.title)")
            }

``` 
