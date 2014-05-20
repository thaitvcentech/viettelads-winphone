Hướng dẫn cài đặt Viettel Ads SDK.

1. Add Banner Ads.

Hiển thị quảng cáo dưới dạng banner.
Tìm tới thư mục chứa ViettelAds.dll thêm vào References. 

a. Sử dụng XAML.

Thêm ViettelAds references tới file XAML muốn hiển thị quảng cáo
xmlns:ads="clr-namespace:ViettelAds;assembly=ViettelAds"
Khởi tạo Ads tới nơi bạn muốn hiển thị thành phần bạn muốn hiển thị. 
	<phone:PhoneApplicationPage
   	    ……………………………………………………….
    xmlns:ads="clr-namespace:ViettelAds;assembly=ViettelAds"
    shell:SystemTray.IsVisible="True">

    <!--LayoutRoot is the root grid where all page content is placed-->
    <Grid x:Name="LayoutRoot" Background="White">
        

        <ads:BannerAds VerticalAlignment="Bottom" AppID="MY_APP_ID" />
        
    </Grid>

</phone:PhoneApplicationPage>

b. Sử dụng C#.

using ViettelAds;

namespace ViettelAds_Demo
{
    public partial class BannerAdsPage : PhoneApplicationPage
    {
        BannerAds _banner; 

        public BannerAdsPage()
        {
            InitializeComponent();


            _banner = new BannerAds()
            {
                AppID = "MÃ ỨNG DỤNG"
            };

            LayoutRoot.Children.Add(_banner);

            _banner.LoadAd(new AdRequest());

        }
    }
}



2. Full Banner Ads

Hiển thị loại quảng cáo full màn hình. 

using ViettelAds;

namespace ViettelAds_Demo
{
    public partial class MediaPage : PhoneApplicationPage
    {
        private InterstitialAd interstitialAd;

        public MediaPage()
        {
            InitializeComponent();

            interstitialAd = new InterstitialAd();
            interstitialAd.AppID = " MY_APP_ID";
            interstitialAd.AdsType = FullAdsType.FullAds;

            interstitialAd.ReceivedAd += OnAdReceived

            interstitialAd.LoadAd(new AdRequest());
        }

        private void OnAdReceived(object sender, EventArgs e)
        {
            System.Diagnostics.Debug.WriteLine("Ad received successfully");
            interstitialAd.ShowAd();
        }
    }
}


